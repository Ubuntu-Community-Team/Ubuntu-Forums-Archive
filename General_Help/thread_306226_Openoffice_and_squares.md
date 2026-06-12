---
title: "Openoffice and squares"
date: 2006-11-24
forum: General Help
---

### Post by mazu on 2006-11-24
Hi,
I'm having some trouble with OpenOffice, there are squares instead of letters in program interface. I found threads saying that the problem is the ia32-libs-gtk, but my machine is not 64 bit (it's intel centrino). I don't know if OpenOffice works earlier becouse I didn't need to use it before.

[[IMG]http://img238.imageshack.us/img238/8092/screenbt8.th.jpg[/IMG]](http://img238.imageshack.us/my.php?image=screenbt8.jpg)

What could have caused this problem???

---

### Post by mazu on 2006-11-25
I'm posting today more info about problem.

Here is the program output:

> 
(process:4910): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:4910): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:4910): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:4910): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:4910): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:4910): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed


I think that maybe I've removed some crucial package... does anybody know which package it could be?

---

### Post by bikeboy on 2006-11-25
Hmmm very odd. What system font are you using? Maybe try another one to see if it makes any difference. Also try a re-install of OOo using the package manager (can't remember the kde one).

---

### Post by mazu on 2006-11-25
Thanks for your reply.

Hmmm, I'm using Opensymbol font, and gtk2-qt-engines. Is it possible to run apt-get only to check the dependencies of all installed packages?

---

### Post by mazu on 2006-11-25
OK, I've solved the problem. The problem was a system font, I changed it to different one and everything begins to work well. 

EOT

---

