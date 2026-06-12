---
title: "Ubuntu 6.06 x 64, sudo  is owned by uid 777"
date: 2007-05-18
forum: General Help
---

### Post by hezem on 2007-05-18
Heya!

I hitted my head to wall in solving this tricky issue. I goofied something with this ubuntu and now sudo is not responding anymore. When ever I try to use it sudo claims:" sudo: /etc/sudoers is owned by uid 777, should be 0" 

I found hint that it should be solved by using su...but ofcourse  I've no idea about su's password... I tried to boot in rescue mode with Ubuntu cd, but somehow it didn't work either... 


So all help is appreciated:)

-Heikki

---

### Post by PilotJLR on 2007-05-18
Reboot and press "e" when grub loads... "e" is for edit.
Take whichever kernel you normally boot, and add the word "single" at the end of the line in grub, then press enter.

This will boot to single user mode... (command line only). Change the permissions on /etc/sudoers, then reboot normally!

---

### Post by hezem on 2007-05-18
Hey

Others fine, but I've no boot loaders in here. I tried to clikity click the letter e, while the machine was booting few rounds but it didn't go to anywhere.

I also tried to use command single when booting with cd, but it didn't go anywhere either.

I only have ubuntu installation on that pc, nothing else and GUI is down as well... but I'm quite sure that I can solve that out as soon as I manage to fix this sudo-issue.

---

