---
title: "Update Manager Problem: Won't Run"
date: 2008-06-17
forum: General Help
---

### Post by kalbir on 2008-06-17
Hi All,

I've been having a problem with the Update Manager. I upgraded from 7.04 to 7.10 today with the intention to then go to 8.04. However, since I have got to 7.10 I have been unable to start the update manager. When I do in the terminal I get the following:

> ****@****:~$ gksudo update-manager -d
No ask_pass set, using default!
xauth: /tmp/libgksu-rGhQ57/.Xauthority
/home/****/.themes/Nova-Blue/gtk-2.0/gtkrc:1765: error: invalid string constant "SPbutton", expected valid string constant
STARTUP_ID: gksudo/update-manager/18424-0-****_TIME2543342453
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: update-manager
buffer: -Traceback (most recent call last):-
buffer: -  File "/usr/bin/update-manager", line 28, in <module>-
buffer: -    import gtki-
buffer: -  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>-
buffer: -    from gtk import _gtks-
buffer: -  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module><-
buffer: -    from _cairo import *.-
buffer: -ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents-
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
brute force GNOME_SUDO_PASS ended...
No password prompt found; we'll assume we don't need a password.
xauth: /tmp/libgksu-rGhQ57/.Xauthority
xauth_env: /home/****/.Xauthority
dir: /tmp/libgksu-rGhQ57


Any ideas as to what is going on?

Best,

Kalbir

---

### Post by kalbir on 2008-06-17
Update: 

If I run with just "sudo" rather than "gksudo" I get the following:

> ****@****:~$ sudo update-manager -d
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 28, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents


---

### Post by Fingel on 2008-06-17
Try using a different GTK theme. It looks like it might be causing some problems.

---

### Post by kalbir on 2008-06-17
Tried changing the theme and deleting the theme folder that it quotes, doesn't make any difference except to scrub that line from the message.

---

### Post by kalbir on 2008-06-18
Bump?

---

### Post by kalesh7 on 2008-06-18
your problem is with cairo that much I can say, but I don't know what the fix should be. maybe a reinstall of cairo?

---

### Post by kalbir on 2008-06-18
Thanks Kalesh, I've tried reinstalling the Cairo libs with no luck. Not sure what to do next!

---

### Post by kalbir on 2008-06-19
Bump:(

---

### Post by tolight on 2008-06-29
I have exactly the same problem but still have no fix. Any help will be greatly appreciated. Do you also see a red circle with a white bar sign in the manu bar on the top?

---

### Post by tolight on 2008-06-29
Hi, I found the trick in the other post. You can run:

sudo apt-get update
sudo apt-get upgrade

to fix this problem. I tried them and they did solve my problems.:)

---

