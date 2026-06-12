---
title: "Messing with grub booting..."
date: 2005-08-16
forum: General Help
---

### Post by audax321 on 2005-08-16
Hey, I was just wondering if it was possible to tell grub to load a particular operating system on the next boot. I know in Lilo, it was possible to issue the following:

/sbin/lilo-R windows /usr/bin/reboot

to cause whatever you have labeled as "windows" in lilo.conf to automatically load on the next reboot, but I'm unsure if grub has this functionality. I always reboot expecting to go into Windows to play a game or do something, then wander off and forget about the grub menu so it would be nice to just make a script and throw it on the desktop to automatically reboot into Windows.

---

### Post by audax321 on 2005-08-16
nevermind, found it.. the command is called:

grub-reboot

I really need to stop posting threads that I answer myself a few minutes later  ;-)

---

