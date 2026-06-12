---
title: "desktop not loading (.Xauthority)"
date: 2020-12-03
forum: General Help
---

### Post by waterdoc on 2020-12-03
hi, I'm a newbie to linux.  I installed Ubuntu 20.04.1 LTS on my older MacBook Pro 6.2 (p4, i7). It was working well for some time.

Now, when i startup my laptop i get to the first screen and enter my p/w.  I then get a blank screen.

I can access the system (alt ->) and login with my login and p/w information.

When i try 'startx' i get the blank screen again.

When i try to load a Lightdm file ([https://unix.stackexchange.com/questions/170650/ubuntu-does-no-let-me-log-in-to-my-user-how-can-i-fix-it](https://unix.stackexchange.com/questions/170650/ubuntu-does-no-let-me-log-in-to-my-user-how-can-i-fix-it)) i get the message:[INDENT]E: you don't have enough free space in /var/caches/apt/archives/[/INDENT]

As a super user (sudo -s), xstartx' works and i get into the desktop as a superuser.  All my files are there...i just can't login and get my desktop as usual -- i really would like to be able to access my old email account and sticky notes (which i did not back-up).

help!

---

### Post by grahammechanical on 2020-12-03
I am assuming that the first screen that you mention is the standard Ubuntu login screen. If Ubuntu is the only OS on this machine you will not see the Linux boot menu (Grub). To load that menu follow the instructions here

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

The method is different for a BIOS motherboard compared to a UEFI motherboard.

At the Grub boot menu you select Advanced options for Ubuntu and select an alternative Linux kernel to load. May be loading a different kernel will produce a more acceptable result.

Ubuntu does not use LightDM any more. Ubuntu uses GDM3. If we get to a login screen then GDM3 has successfully loaded and has done its job of providing the login screen.

From the Grub menu>Advanced options we can chose a Linux kernel with recovery mode. That should load to a recovery menu. If we chose Resume Ubuntu should load with a basic video mode. If this happens then the problem may be the video driver.

Regard

---

