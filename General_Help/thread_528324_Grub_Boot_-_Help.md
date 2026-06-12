---
title: "Grub Boot - Help"
date: 2007-08-17
forum: General Help
---

### Post by MattJones2k6 on 2007-08-17
Hey,

When i used the live CD i needed to change my VGA res to 1024x786...

When on GRUB load up i think it uses a higher res that my monitor can't support....

How do i set the launch options for it to change res?

Thnx.

---

### Post by jamvegan on 2007-08-17
You can edit /etc/X11/xorg.conf (it is easy to make changes to this file that will prevent X from starting, so I always make a backup copy before changing it).  Comment out (with a # at the beginning) any lines in the "Screen" section of the file with modes higher than 1024x768.  Hope that helps!

---

