---
title: "Gnome: Scroll Wheel Lines"
date: 2007-12-11
forum: General Help
---

### Post by BlueFiberOptics on 2007-12-11
In KDE's mouse options, I am able to set the lines scrolled by the mouse scroll wheel from 3 to 6.  I am unable to find this option in Gnome and would really appreciate a way to change it.  

Does anyone know how I could change the lines?

---

### Post by the_cog on 2007-12-14
Whatever you do, DON'T add the following to /etc/X11/xorg.conf

Option         "VertScrollDelta" 6

It crashes X.

---

### Post by pinow on 2007-12-16
There's already a topic about it:
[http://ubuntuforums.org/showthread.php?t=628725](http://ubuntuforums.org/showthread.php?t=628725)

---

### Post by BlueFiberOptics on 2007-12-16
> **pinow said:**
> There's already a topic about it:
[http://ubuntuforums.org/showthread.php?t=628725](http://ubuntuforums.org/showthread.php?t=628725)

Thanks for the link, but that topic talks about adding a specific line to xorg.conf which ends up crashing it.

---

### Post by pinow on 2007-12-28
> **BlueFiberOptics said:**
> Thanks for the link, but that topic talks about adding a specific line to xorg.conf which ends up crashing it.
If you check the link to the other thread again, you'll see it got fixed :)

syntax error ](*,)

---

