---
title: "textual login to window maker"
date: 2007-03-03
forum: General Help
---

### Post by gala.martin on 2007-03-03
Hi folks,
 I am a young-but-old-fashioned "ubuntian", so that I mainly use the window maker (or similar) interface, I avoid splash boot and, of course, use an old fashioned pc. There are just a couple of things falling out this picture. The first one, is that I used linux for several years, but I never learnt  how it works. The second one is gdm (GNOME Display manager).

I would like to have a textual login at boot, but if I disable the gdm daemon I am able to run only the Xfce interface via
```
$startx
```
I guess I should add some options to start a different interface, but I do not know which ones, and the manual did not help me. I would like to set things up so that
-if I run startx, a default interface (that I decided) starts
-if I run startx -something, another interface (depending on "something") starts
-no display manager is loaded

Even better, although I am not sure this can be smoothly achieved, I would like to have  a textual login like this

PCname login: [[I TYPE MY USERNAME]]
Password: [[I TYPE MY PASSWORD]]
GUI:
Press Enter for default (WM)
Press <0> for shell (no GUI)
Press <1> for GNOME
Press <2> for GNOME failsafe
etc
[[I HOPEFULLY PRESS THE RIGHT NUMBER FOR THE WANTED INTERFACE]]


and then having a file/directory somewhere, in which I can decide what is default and possibly other options.

Thanks a lot

---

### Post by nereid on 2007-03-03
Which window manager will be started with startx depends on the content of the .xinitrc file in your home directory.

```

exec windowmaker

```

Will start windowmaker (or was it wmaker?). For GNOME the entry is *exec gnome-session*.

**Edit:**
It is the .xinitrc file.

---

### Post by gala.martin on 2007-03-03
Thanks for the answer, nereid.

The only code exec recognize is
```
exec wmaker
```
(if I exec "windowmaker" or "exec wm", exec tells me it does not know them)

Anyway, I get an error also when I "exec wmaker". Here it is
```

/usr/lib/WindowMaker/WindowMaker fatal error: could not open display ''''

```

Any suggestion?

---

### Post by nereid on 2007-03-03
No, this code has to be in the *.xinitrc* file. Then you just type startx and this will take a look at you .xinitrc file.

---

### Post by gala.martin on 2007-03-03
Thanks again.

This is my/etc/X11/xinit/xinitrc file#!/bin/sh
# $Xorg: xinitrc.cpp,v 1.3 2000/08/17 19:54:30 cpqbld Exp $

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession

So it seems the trouble should be in Xsession, that is a too complex file to bother you with, here. I may have some time in the next days to try to fix this somehow. If I work something out, I may post it. 

Incidentally, how much memory is expect to require a just loaded Xfce system? Mine is using more than 300Mb (from "top"); it seems way too much, and it is also quite critical for my system.

---

### Post by nereid on 2007-03-03
No, this is the global xinitrc file. Just create on in your home folder with the above mentioned content. Do NOT touch the global file.

---

### Post by gala.martin on 2007-03-04
I have solved like this. I created a .xinitrc file in my home directcory, containing
```
xterm -geometry 80x20+494+51 &
exec wmaker
```

and a file .gdm contaning

```
sudo /etc/init.d/gdm start
```

I disabled gdm at startup. Now I have a textual login. If I type ```
startx
```, window maker starts. If I want to start some other gui, I type ```
. .gdm
```, and I can use gdm. Not very elegant, but effective. Thx Nereid for your help.

---

