---
title: "Lost both of my OS"
date: 2007-05-12
forum: General Help
---

### Post by mvashi on 2007-05-12
I have Win Xp on my first hard drive and Ubuntu 7.04 on my second.It is a dual boot system and to my horror my second hard drive failed on which Ubuntu was installed.Now when I try to choose Win Xp as the OS to boot to , it goes past the opening screen  and then just hangs.when I disconnect the second hard drive and restart the PC , i get the error message which goes something like this
Grub 
Error 21 

Is there any way to disable the dual boot utility till I get a new Hard drive ?

---

### Post by strayduck_uk on 2007-05-12
When GRUB is broken I always use the Windows XP installation disk.

Boot from the Win XP CD, and when prompted about what you want to do choose to use the Recovery Console (think you have to press R).

Then you need to "logon" to your Windows installation - you'll be prompted to do this but you will need your ADMINISTRATOR password

Then issue the command fixmbr    - answer yes to whatever blurb comes up.

This will overwrite GRUB and will allow Windows XP to start as default.

It will mean that you will have to reinstall GRUB when you get a second hard disk, but I suspect you will end up installing Ubuntu again anyway.

Hope this helps.

---

### Post by UbuntuniX on 2007-05-12
The easiest solution would be to boot a Ubuntu LiveCD and install GRUB to the MBR.

Use these guidelines ([https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)).

---

### Post by mvashi on 2007-05-12
Thank you for your very quick reply.
Frankly I am very impressed. Wow!!! just minutes into posting the problem and I get a reply !!!!
If I had my way I would just delete the XP and install Ubuntu instead , but then there are other users in the family and they not too keen to leave their comfort zone, specially the better half !!!!

---

