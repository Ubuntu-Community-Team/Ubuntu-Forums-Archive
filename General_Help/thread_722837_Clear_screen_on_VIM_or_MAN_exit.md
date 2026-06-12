---
title: "Clear screen on VIM or MAN exit"
date: 2008-03-12
forum: General Help
---

### Post by jerrydav on 2008-03-12
Hi !

When I exit VIM or a man page, the content of the file or the man page stay printed in the console. I was used to have my screen reset back to what it was before entering VIM or a man page (like in other distro), and I find it quite annoying. Someone knows how to do this ?

I've search for this for a while but found nothing so far. I don't think I use the proper search keywords. ;)

Thanks,
Jerrydav

---

### Post by Mikes80 on 2008-03-12
What console are you using? I don't have this problem with gnome terminal. To clear the screen use;

```
clear
```

at the command prompt after you exit the programs.

Edit: Just realised you may have meant the tty console. I'm not sure how you can get this to clear automatically. Perhaps you could get in touch with the distro's it worked on and find out how they implemented this.

---

### Post by pointone on 2008-03-12
You could easily create a wrapper script for "vim":

```
#! /bin/bash

/usr/bin/vim $* && clear
```

---

### Post by jerrydav on 2008-03-13
Well I don't really mean clear all the screen, but get back to the screen like it was before entering vim. In Ubuntu, when I quit VIM, I can still see the content of the file edited by VIM, instead of seeing my previous shell commands.

Well I might not be very clear, so here is an example:

If I do the following commands:
[~/temp]$ touch file1.txt
[~/temp]$ touch file2.txt
[~/temp]$ ls
file1.txt  file2.txt
[~/temp]$ vim file1.txt

And then write "blabla" in my file1.txt, save it and exit. Here is the content of my shell screen in Unbuntu:

------------------------------------------
blablabla
~
~
~
~
[~/temp]$
------------------------------------------

And here is want I want to see in my screen:

------------------------------------------
[~/temp]$ touch file1.txt
[~/temp]$ touch file2.txt
[~/temp]$ ls
file1.txt  file2.txt
[~/temp]$ vim file1.txt
[~/temp]$
------------------------------------------

I hope I made myself a little bit clearer. ;)
Jerrydav

---

### Post by pointone on 2008-03-13
I think I know what you're talking about now, and I don't think it's Vim-exclusive. Distros that I've seen that on also have the same behaviour for reading man pages or using more. May be a console/terminal setting.

I'm curious about this now, too!

---

### Post by jerrydav on 2008-03-14
Finally I found the answer! It is somehow related to the termcap / terminfo configuration. 

Instead of using "xterm" terminal emulation, I should use "rxvt".

```
export TERM=rxvt
```

This will do the job.

Here is the link that pointed me to the right direction : [http://www.dc.turkuamk.fi/docs/soft/vim/vim_tips.html#xterm-screens]("http://www.dc.turkuamk.fi/docs/soft/vim/vim_tips.html#xterm-screens").

Following the informations in that link, using this command : "infocmp -C xterm" showed me that xterm does not use 47l and 47h code, but some 1049l and 1049h codes (I have no idea what they are). But printing the rxvt capabilities with "infocmp -C rxvt" showed me this one supports what I was looking for.

Thanks for your help,
Jerrydav

---

