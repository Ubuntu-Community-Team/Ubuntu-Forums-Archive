---
title: "GRUB won't load Ubuntu 8.04"
date: 2008-06-09
forum: General Help
---

### Post by cnekmp on 2008-06-09
Hi, i have a problem. I wanted to change GRUB boot loader to the [GRAPHICAL ONE]("http://ubuntuforums.org/showthread.php?t=208855"), but i could see only text based GRUB. Then i made changes to my menu.lst file and wrote: 
```
gfxmenu /grub/message.suse
```
instead of
```
gfxmenu /boot/grub/message.suse
```
So, when computer boots up, it throws me to the GRUB command line, and Ubuntu won't start.
I tried to fix MBR and typed commands:

[B]grub> find /boot/grub/stage1
(hd0,5)
grub> root (hd0,5)
grub> setup (hd0)[/B]

Shows that Stage1, Stage2, menu.lst has been updated successfully without any problem. Then i reboot, but it throws me to the grub console again.
I think that i need to edit menu.lst file, and delete the first line somehow:
gfxmenu /grub/message.suse

What can i do in this case?

---

### Post by Titan8990 on 2008-06-09
You can change your menu.lst file from the Ubuntu live CD. It looks like you specified an incorrect path and will need to change it back.

Here is a quick step by step that assumes that your boot partition is sda1

Boot into the live CD.

$sudo mkdir /media/sda1

$sudo mount /dev/sda1 /media/sda1

You can now navigate to /media/sda1 via nautalus or the terminal. From there you should be able to change your menu.lst file.

---

### Post by cnekmp on 2008-06-10
> **Titan8990 said:**
> You can change your menu.lst file from the Ubuntu live CD. It looks like you specified an incorrect path and will need to change it back.

Here is a quick step by step that assumes that your boot partition is sda1

Boot into the live CD.

$sudo mkdir /media/sda1

$sudo mount /dev/sda1 /media/sda1

You can now navigate to /media/sda1 via nautalus or the terminal. From there you should be able to change your menu.lst file.

**Thank you very much Titan8990 :)**

It was very easy to repair GRUB, as i made backup copy of GRUB folder to my disk before uninstalling it, so i just did:

1. Booted OS from Ubuntu Live CD.
2. Run these commands in Terminal:
```
sudo cp -r /media/disk-1/grub /media/disk/boot/
sudo grub
root (hd0,5)
setup (hd0)
```
3.Rebooted to the main system.

P.S. Actually latest versions of Ubuntu Live CD's detects media disks (NTFS, FAT, etc.) without mounting them, so i did no one of your commands ;)

**SOLVED**

---

### Post by Titan8990 on 2008-06-10
Even though my instructions didn't specifically fix your problem I am glad I was able to get you moving in the right direction.

---

### Post by cnekmp on 2008-06-12
But thank you a lot for giving me that idea :)

---

