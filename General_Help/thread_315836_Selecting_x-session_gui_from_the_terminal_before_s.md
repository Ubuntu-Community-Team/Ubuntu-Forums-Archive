---
title: "Selecting x-session gui from the terminal before starting X?"
date: 2006-12-09
forum: General Help
---

### Post by kd7swh on 2006-12-09
what command should I use to change GUIs before starting X? (my desktop manager is the terminal)

startx just launches Gnome (default) but I want to be able to switch in between GUIs.

---

### Post by hytek on 2006-12-09
isn't it just kdm or gdm?

/etc/init.d/kdm start

eh I forget. could be way off to ](*,)

---

### Post by kd7swh on 2006-12-09
I could start kdm or gdm, but do I have too? Can I select a gui from the terminal without running a gui-based desktop manager?

---

### Post by lloyd_b on 2006-12-09
As I understand it, the file "~/.xsession" controls which desktop is loaded.  If you don't have such a file, then it falls back to the default "/etc/X11/Xsession".

Under Debian Sarge, I had Gnome as a default, but if I copied "/usr/bin/startkde" to "~/.xsession", then "startx" would run KDE instead.
I haven't tried this under Ubuntu, however...

Lloyd B.

---

### Post by kd7swh on 2006-12-09
I don't have a .xsession file but I have a .xsession-errors file. lol

---

### Post by kd7swh on 2006-12-09
could someone give me an example ~.xsession file? I would just make one if I knew what was included.

---

### Post by lloyd_b on 2006-12-09
xsession files are pretty complex.  Take a look at "/etc/X11/Xsession" and you'll see what I mean.

Which desktop are you trying to start?  Most desktops already have a file that's suitable for copying/linking to "~/.xsession" (/usr/bin/gnome-session for Gnome, /usr/bin/startkde for KDE, etc).

Lloyd B.

---

### Post by kd7swh on 2006-12-11
I just made an ~.xinit file. In my home directory. 
something like:

exec fluxbox 

or 

exec gnome-session

and it launched what ever gui I put in the first line. :-D

---

