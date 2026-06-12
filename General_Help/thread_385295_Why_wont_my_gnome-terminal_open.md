---
title: "Why wont my gnome-terminal open?"
date: 2007-03-15
forum: General Help
---

### Post by mesach on 2007-03-15
When i try to run terminal in Gnome, it just sits at starting terminal for a few seconds and then just dissapears... I've tried to re-install it using synaptic, even completely removed it, and then installed it again, and it does the same thing.

I'm pretty new so I dont know of any other terminal's to use, except Konsole, but i dont like the shift+insert to paste and a few other things about it, plus the fact that its not installed at the moment... I want my gnome terminal back...

Any suggestions?

---

### Post by schilcha on 2007-03-15
Open konsole or xterm and launch gnome-terminal from within there. See, if there are any messages displayed that help you with your problem.

---

### Post by mesach on 2007-03-15
Thanks for that tip! Here's what was output

The program 'gnome-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 108 error_code 2 request_code 78 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Looked up the error and found out that Xinerama breaks Gnome-terminal

Here's the WORKAROUND for anyone looking for it
[https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232](https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232)

add this to your xorg.conf
#------------------------------------------
Section "Extensions"
Option "Composite" "false"
EndSection
#------------------------------------------

---

### Post by gmcle454 on 2007-04-11
Thanks, I don't know what caused it, but that worked for me too.

---

