---
title: "Windows keeps overwriting grub"
date: 2006-12-24
forum: General Help
---

### Post by azidrane on 2006-12-24
I've got a problem thats been bugging me for a while.

I have a 200GB SATA2 drive with windows xp and ubuntu installed. First I had Windows installed. When I instaleld ubuntu, I moved the windows XP partition to the end of the drive and installed ubuntu at the start. After reboot the comp loaded grub with the choice of windows or ubuntu. Loading Ubuntu is fine. Then I reboot and go to grub and load windows. Windows loads fine. THen I reboot, NO GRUB!
So I throw the Ubuntu CD into the drive and reboot, select to "Boot from first hard disk" and BAM, back to grub, but now it wont load Ubuntu. So I edit the boot commands from grub and see that now grub thinks that my hd2 is my hd0 and vice versa. So i fix that and i'm in linux. Reboot, NO GRUB. back to live CD, first HDD, back to grub and into linux. BUT when I boot w/o the CD in the drive, it goes straight to windows.

HELP ME!

---

### Post by goatflyer on 2006-12-24
Its hard to tell from your post, but at least I can tell you Windows likes/prefers/insists on being the first partition.  So let it.

Then Install Ubuntu ext3 partitions / and swap after, let grub write to MBR.
grub will allow you to boot windows or ubuntu.

---

### Post by meng on 2006-12-24
That's one way, OR you can do this without reinstalling all of Ubuntu:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

