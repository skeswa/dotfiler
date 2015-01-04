Dotfiler
========
Dotfiler is a righteous command-line dotfile management utility that allows you to manage your personal environment configuration and take it with you wherever you go.

# Installation
**TODO** write out instructions for this. lolololol.

# Getting Started
Getting going weith dotfiler is pretty straight forward. All you have to do is ```dotfiler init``` anywhere in your filesystem, and you'll be prompted to setup a github repository for all your dotfiles. Dotfiler will then ask you which dotfiles you want it to keep track of and remember.
### Tracking Dotfiles
Whenever you want dotfiler to start tracking a dotfile, simply use ```dotfiler track```. For example, if I wanted to start tracking my `.vimrc`, so that I could keep track of my vim configuration, then I would just type into my shell 
```sh
$ dotfiler track .vimrc
``` 
You may have noticed that dotfiler just _assumes_ that you're talking about your home directory. So, `.vimrc` is simply interpreted as `~/.vimrc`.
### Untracking Dotfiles
To get dotfiler to stop tracking a file, ```dotfiler untrack``` will do the trick. To continue with the previous example, if I wanted dotfiler to forget about my `.vimrc`, I would intuitively type
```sh
$ dotfiler untrack .vimrc
```
### Syncing Dotfiles
If your dotfiles are changed remotely, or if you simply are setting up in a fresh environment, all you have to do is call ```dotfiler sync```. Dotfiler will take care of the rest, asking you to resolve any conflicts in a swift and efficient manner.

# Connecting Remotely
Dotfiler can be used to copy your dotfiles over during SSH connections, which makes it really handy for people who find themselves remoting often. Using dotfiler over SSH is pretty intuitive, all you have to do is ```dotfiler ssh```, and then include any arguments that you would normally include with the normal SSH command. For instance, if I wanted to connect to to my server with the URL `foo.bar.baz` over SSH, and I also wanted the logging to be verbose, I would simply execute 
```sh
$ dotfiler ssh -v guy@foo.bar.baz
``` 
This starts an SSH session, as would be expected, but at the beginning of the session, dotfiler prompts you before downloading your dotfiles locally and setting up your environment. This initial downloading, of course, happens exactly once. Thereafter, dotfiler just updates your dotfiles on the remote system when necessary.

# Borrowing Dotfiles
With ```dotfiler borrow```, you can grab other people's dotfiles to try them out. Then you can either ```dotfiler revert``` to go back to your own dotfiles, **or** you can claim them as your own with ```dotfiler keep```. In this example, I want to try out `@samuelcouch`'s dotfiles (`@samuelcouch` referring to the GitHub user samuelcouch).
```sh
$ dotfiler borrow samuelcouch
```
Then, afterwards, I discover that `@samuelcouch`'s dotfiles _suck_, so I decide I want to get rid of them.
```sh
$ dotfiler revert
```
I'm now back to where I started, but lets say I see `@skeswa`'s dope-ass dotfiles and decide they're so awesome that I want to keep them indefinetely.
```sh
$ dotfiler borrow skeswa
$ dotfiler keep
```
`@skeswa`'s are now remembered as my dotfiles by dotfiler. This means that ```dotfiler revert``` will no longer take me back to where I was. However, if you really want to go back in time, you can always use ```dotfiler rewind```. For example,
```sh
# This goes back in time to 2 hours ago
$ dotfiler rewind 2 hours
# This goes back in time to 1 day before that
$ dotfiler rewind 1 day
# This goes back in time 1 week before that
$ dotfiler rewind 1 week
```
Keep in mind though, that **the rewind command is permanent**. Once ```dotfiler rewind``` is called, there is no going back to the future (_teehee_) again, all un-backed-up changes are 100% lost.

# Todo's

 - Figure out the nuances of Rust
 - Literally Everything
 - Write Tests

# License
The MIT License (MIT)

Copyright (c) 2014 Sandile Keswa

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
