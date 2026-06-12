---
title: "Ubuntu to Windows partition editing"
date: 2008-01-04
forum: General Help
---

### Post by brianbjjohnson on 2008-01-04
I needed to know how to load Windows XP Media Edition and run a dual boot system with it. Basically, I need to run a program on Windows for my school, but only have Ubuntu. I need to know how to run Ubuntu and Windows on a dual boot system... But have to do it through Windows. Y'know what I mean? Well if anybody could help that would be great... I kinda need this by Noon, Sunday.

---

### Post by PeterJS on 2008-01-04
That's the thing about a dual boot, you're on what ever system you choose to boot to, if you mean using ntldr to chainload in to grub, I've heard that it's theoretically possible, but never heard anything good about it. Is there a specific reason not to have grub as the primary boot loader?

Anyway on to the instructions:
First use a livecd to shrink ubuntu
Install windows
Reinstall grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Reconfigure grub to include an option to boot windows, this may involved having grub remapping drives as windows get very upset about not booting off of partition 0

---

