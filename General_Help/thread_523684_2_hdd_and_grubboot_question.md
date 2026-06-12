---
title: "2 hdd and grub/boot question"
date: 2007-08-12
forum: General Help
---

### Post by df9517 on 2007-08-12
I have two HDD, one large and one small. I have installed Ubuntu using the whole large HDD (sdb1). The small HDD (sda1) is to be used for backup/storage only.

I think that the computer boots from the small HDD and from that grub start Linux installed on the large one. I am hpwever not 100% sure and do not know how to check it.

The thing is that I would like to change the small one but I am very worried that I then will delete/remove grub/boot from the computer so that nothing will start up. 

So how can I check about actual situation? How can I do to remove the small HDD?

Below are the info of my HDD's.

Regards,
Daniel


Disk /dev/sda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4982    40017883+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29650   238163593+  83  Linux
/dev/sdb2           29651       30401     6032407+   5  Extended
/dev/sdb5           29651       30401     6032376   82  Linux swap / Solaris

---

### Post by chewearn on 2007-08-12
Two possible way to check for sure:
1. Go into your BIOS and see which HD is the boot disk; normally by either pressing F2 or DEL during the BIOS POST screen.  Depending on your BIOS menus, it could be straight forward or need some figuring out, which HD is the boot disk.

2. Temporarily unplug the smaller HD from your compter, and see if it still boot to ubuntu; if it does, then you are home free.  If does't boot, the GRUB is located in the smaller HD MBR, and you need to reinstall GRUB into the larger HD MBR.

[https://help.ubuntu.com/community/Re...ct=RestoreGrub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by df9517 on 2007-08-13
Thanks for your reply. Seems like grub is installed on the smaller HDD.

Why is Ubuntu installing grub on a different HDD than the one I install the program to. I think I should at least be able tp choose that during the installation.

Anyway, I will study how to install grub on the big HDD.

Thanks

---

