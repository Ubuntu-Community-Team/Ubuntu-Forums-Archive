---
title: "Bootup w/no monitor - gets only 680x400 resolution using  remote desktop"
date: 2007-05-09
forum: General Help
---

### Post by rocket777 on 2007-05-09
I've got a ubuntu system with no monitor attached and access is via remote desktop (vncviewer). Basically, it's just a box with a network card - no keyboard, mouse, or monitor. Everything works, except when using it remotely, it only has 680x400 screen resolution.

I read a post that said one could turn off monitor auto-detection and this would fix the problem. But I can't figure out how to do this.

Any help would be appreciated?

---

### Post by sinfree on 2007-05-10
First, make a backup of your /etc/X11/xorg.conf file (I usually just make a copy of it and call xorg2.conf).  For turning off the auto detection of the monitor run the setup:

```
sudo dpkg-reconfigure xserver-xorg
```

Of course, be careful when going through that wizard as you can make is so that your system will not boot into X (that is why you backup the xorg.conf file).  Most of the defaults in the should be fine, it should eventually ask about your monitor, and you can tell it whether to auto detect or not.  Tell it not too, then it will give you the chance to set the monitor settings yourself.

Let me know how that works.

---

