---
title: "Starting vim in non-compatibility mode"
date: 2013-08-16
forum: General Help
---

### Post by newb85 on 2013-08-16
I've been going through a tutorial on the command line, and it suggests that I should be able to start Vim in normal mode by simply
```
vim
```
but all I get is 
```
The program 'vim' can be found in the following packages: * vim
 * vim-gnome
 * vim-tiny
 * vim-athena
 * vim-gtk
 * vim-nox
Try: sudo apt-get install <selected package>
```

Now I would think this means Vim isn't installed on my system.  Yet when I run
```
vi
```
I get
```
~                                                                               
~                                                                               
~                              VIM - Vi IMproved                                
~                                                                               
~                               version 7.3.547                                 
~                           by Bram Moolenaar et al.                            
~           Modified by pkg-vim-maintainers@lists.alioth.debian.org             
~                 Vim is open source and freely distributable                   
~                                                                               
~                        Help poor children in Uganda!                          
~                type  :help iccf<Enter>       for information                  
~                                                                               
~                type  :q<Enter>               to exit                          
~                type  :help<Enter>  or  <F1>  for on-line help                 
~                type  :help version7<Enter>   for version info                 
~                                                                               
~                        Running in Vi compatible mode                          
~                type  :set nocp<Enter>        for Vim defaults                 
~                type  :help cp-default<Enter> for info on this                 
~                                                                               
~                                                                               
~                                                                               

```
and when I run the "set nocp" command it switches Vim to normal mode.  Clearly Vim is installed on my system, so why can't I run it from the terminal as in my first example?

---

### Post by TheFu on 2013-08-16
man vim will explain.
Are you certain that running vi isn't the same as running vim?
On my 12.04 kvm server, 
```
/usr/bin$ ll vi*
lrwxrwxrwx 1 root root      20 May 20  2012 vi -> /etc/alternatives/vi*
lrwxrwxrwx 1 root root      22 May 20  2012 view -> /etc/alternatives/view*
lrwxrwxrwx 1 root root      21 May 20  2012 vim -> /etc/alternatives/vim*
-rwxr-xr-x 1 root root 2015392 May  4  2012 vim.basic*
lrwxrwxrwx 1 root root      25 May 20  2012 vimdiff -> /etc/alternatives/vimdiff*
-rwxr-xr-x 1 root root  777056 May  4  2012 vim.tiny*
-rwxr-xr-x 1 root root    2084 May  4  2012 vimtutor*

``` and 
```
/etc/alternatives$ ll vi*
lrwxrwxrwx 1 root root 18 May 20  2012 vi -> /usr/bin/vim.basic*
lrwxrwxrwx 1 root root 18 May 20  2012 vim -> /usr/bin/vim.basic*

```

So, it seems that I don't have the full vim installed either. Never noticed, as long as **nano is NOT the default**, I'm happy.

---

### Post by newb85 on 2013-08-16
"Running in Vi compatible mode" makes me think it's not the same. 

On Ubunintu, vim-tiny is installed (rather than vim-basic as on your system).

Regardless of which Vim is installed, I don't see why it can't be launched  regular mode, since it can be switched to regular mode once it's launched.

---

