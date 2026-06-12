---
title: "Compiling vim 7 under Dapper"
date: 2007-06-13
forum: General Help
---

### Post by andrew.46 on 2007-06-13
Hi,

 Has anybody tried compiling vim 7 under Dapper? I am just about to have a shot at it and would just like to know if there are any special problems. I was going to work from the file:

[ftp://ftp.vim.org/pub/vim/unix/vim-7.1.tar.bz2](ftp://ftp.vim.org/pub/vim/unix/vim-7.1.tar.bz2)

 Thanks for your trouble,

        Andrew

---

### Post by 5-HT on 2007-06-13
Been a while since I built vim7 for Dapper, but I don't remember running into any problems. You can always grab the current vim source from Feisty if you like and build from there instead of using upstream source. Post back if you run into any problems and enjoy the new features!

---

### Post by andrew.46 on 2007-06-15
Hi,

 Wooooo hoooooo! I'm the king of the world:

```
andrew@ilium:~$ vim --version
VIM - Vi IMproved 7.1 (2007 May 12, compiled Jun 15 2007 16:41:04)
Compiled by andrew@ilium

```

 Actually it was incredibly simply, all I was missing was a single dev file: libncurses5-dev. Now I just have to *really* learn how to use the program :-) I am getting what looks like a great Linux book from Amazon shortly:: "A Practical Guide to Linux(R) Commands, Editors, and Shell Programming [Paperback] By: Mark G. Sobell " which among other things has an entire chapter on vim.

                     Andrew

---

### Post by 5-HT on 2007-06-15
To get up and running, vim comes bundled with a little hands-on tutorial as well called 'vimtutor'.

---

