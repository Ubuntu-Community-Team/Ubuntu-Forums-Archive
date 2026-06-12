---
title: "Unable to point GRUB to stage2 on a different partition"
date: 2006-12-27
forum: General Help
---

### Post by jamadagni on 2006-12-27
My current GRUB installation is on sda and the stage2 files are at sda8. But I want to move my Kubuntu installation to sda3 and was successfully able to do so for all files in the partition but I have problems with pointing GRUB to that partition for the stage2 files.

I tried to reinstall GRUB but I am unable.

grub> setup --stage2=/boot/grub/stage2 (hd0,2) (hd0,2)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no
Error 15: File not found

But:

grub> find /boot/grub/stage1
 (hd1,2)
 (hd1,5)
 (hd1,7)

OK so I am trying to install on hd0,2 whereas GRUB sees the files on hd1,2. But I don't understand why, since:

root@chandas:~# cat /boot/grub/device.map
(hd0)   /dev/sda
(hd1)   /dev/hda

and the linux installations are at sda3, sda6 and sda8, I expect the files to be in hd0,2 only. Why is GRUB saying that the files are at hd1,2?

---

