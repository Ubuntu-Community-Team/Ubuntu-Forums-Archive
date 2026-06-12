---
title: "[SOLVED] Various Terminal Programs"
date: 2008-03-13
forum: General Help
---

### Post by Bruce M. on 2008-03-13
OK, this may sound really out to lunch but since I switched to Xfce from Gnome I noticed that I really didn't like **xterm**, I can't cut/paste commands and I'm a 4 finger typist.

So I got **gnome-terminal** because I know it, and I can cut/paste in it.

However as I read different posts in different threads I see mention of various terminal programs.

So I did a search in Synaptic and found these:
(*) installed - ( ) not installed

(*) xterm - can't cut/paste
(*) gnome-terminal - installed for cut/paste
(*) xfce4-terminal - ?? Is this xterm?
(*) aptitude - it's a terminal? or a command?

*Is xterm and xfce4-terminal the same thing?*

OK below are some terminal programs I found.

( ) aterm
( ) eterm
( ) mlterm
( ) mrxvt
( ) multi-aterm
( ) multi-gnome-terminal
( ) pterm
( ) pyqonsole
( ) rxvt
( ) rxvt-ml
( ) terminal.app
( ) xvt

*Do any of there allow cut/paste?* ( OK, I'm sure multi-gnome-terminal will.)

*Can I install them **all** to test them, without them interfering with each other?*

And as an after thought because they showed up when searching for "terminal" just what are thses for?

(*) ncurses-base
(*) ncurses-bin
( ) ncurses-term
( ) ytree - file manager for terminals ? - stumped here!

Can someone shed some light here.
Bruce

---

### Post by chadeldridge on 2008-03-13
well Xterm supports copy / paste as do all of them, but no idea about cut:

copy = shift / ctrl / c
paste = shift / ctrl / v     or shift / insert

---

### Post by PeterJS on 2008-03-13
Ncurses is a library for creating pseudo graphical environments in a terminal, one example of a program that uses nucurses is aptitude. Aptitude isn't a terminal, but rather a command line package manager, it can be used both like apt-get by giving it parameters, or synaptic if you give it no parameters.

As for interfering with each other the various terminals shouldn't, and if they do you should get a hold of the author and complain. 

For copy and paste, try:
ctrl+Insert for copy
shfit+Insert for paste

---

### Post by Bruce M. on 2008-03-13
> **chadeldridge said:**
> well Xterm supports copy / paste as do all of them, but no idea about cut:

copy = shift / ctrl / c
paste = shift / ctrl / v     or shift / insert

> **PeterJS said:**
> Ncurses is a library for creating pseudo graphical environments in a terminal, one example of a program that uses nucurses is aptitude. Aptitude isn't a terminal, but rather a command line package manager, it can be used both like apt-get by giving it parameters, or synaptic if you give it no parameters.

As for interfering with each other the various terminals shouldn't, and if they do you should get a hold of the author and complain. 

For copy and paste, try:
ctrl+Insert for copy
shfit+Insert for paste

Ahhhh, I was using mouse... silly me.
Thanks a bunch guys.
Solved
Bruce

---

