---
title: "Booting iso from hfs+ partition"
date: 2014-06-15
forum: General Help
---

### Post by noorez on 2014-06-15
0 down vote favorite
	

I would like to be able to boot from an ISO stored on an HFS+ partition (the main partition on my macbook pro). Here is what I've done so far:

grub> insmod hfs,
grub> insmod hfsplus
grub> insmod loopback
grub> insmod part_gpt
grub> insmod iso9660
grub> loopback loop (hd0,gpt2)/location/to/img.io
grub> configfile (loop)/boot/grub/loopback.cfg ...

This does not work. tab-complete of the (loop) path does not work. Performing an:

grub> ls (loop)

shows "unknown filesystem type error)

However, this does work (tab-complete and all) if the iso comes from my ext3 partition (correctly sees filesystem type as iso9660)

For particular reasons, I can't have the iso images on the ext3 partition, they need to be kept on the hfs+ partition. What should be done?

---

### Post by yancek on 2014-06-15
See post # 8 at the forum link below.  There is a sample entry I posted which booted TinyCore Linux from ntfs.  You would need to make the appropriate changes in your grub.cfg file and I have no idea if it will work with GPT or HFS.

[http://www.linuxquestions.org/questions/linux-newbie-8/boot-linux-from-ntfs-partition-4175499618/](http://www.linuxquestions.org/questions/linux-newbie-8/boot-linux-from-ntfs-partition-4175499618/)

---

### Post by oldfred on 2014-06-16
Some more examples, but I do not think any are for a MAC.

 This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by noorez on 2014-06-20
bump..


still have not found a solution to this. the above proposed solutions do not work.

---

