---
title: "Set default nice value for xorg?"
date: 2007-10-14
forum: General Help
---

### Post by thefirstM on 2007-10-14
I was wondering if there was any way to set a default nice value for Xorg.  I am running Ubuntu on kind of an old PC, and I have found that the Gnome GUI performs much better if I set the nice for Xorg to -10, but I would prefer to have this done automatically when the PC starts.  Does anyone know of such a way?

---

### Post by jpkotta on 2007-10-14
I think you can do this from gdm's config file.  Looking at the init script for gdm, the file it wants is /etc/gdm/gdm-cdd.conf, which is a symlink to some other file.  In that config file, there is an option:
[QUOTE=/etc/xdg/xubuntu/gdm/gdm.conf]
    546 # Indicates that the X server should be started at a different process
    547 # priority.  Values can be any integer value accepted by the setpriority C
    548 # library function (normally between -20 and 20) with 0 being the default. For
    549 # highly interactive applications, -5 yields good responsiveness. The default
    550 # value is 0 and the setpriority function is not called if the value is 0.
    551 
    552 #priority=0[/QUOTE]
Remember to backup the original config!

---

