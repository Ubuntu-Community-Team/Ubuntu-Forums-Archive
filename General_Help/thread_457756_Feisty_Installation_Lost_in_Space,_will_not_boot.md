---
title: "Feisty Installation Lost in Space, will not boot"
date: 2007-05-29
forum: General Help
---

### Post by flowingfire on 2007-05-29
Hi everybody.  I have a problem.  Feisty simply will not boot.  I'll go over what I did and maybe somebody can help.

What caused this problem is this: I installed a second hard drive.  I then proceeded to install Fedora 7 on the new hard drive.  I instructed the Grub bootloader in the Fedora installation to give me options to boot 3 operating systems: Windows Vista, Feisty Fawn, and Fedora 7.  

Now, the bootloader boots the partitions for Windows Vista and Fedora 7 perfectly fine.  What it cannot do is boot Feisty.  I also checked in Windows, and I cannot access the Feisty partition any longer.

Please help if you know what I can do to be able to get my Fesity back.  The name of the partition it is on is sdb2.  I have Grub set to boot sdb2 as Feisty, but it always give me a error.

Thanks,
-David

---

### Post by confused57 on 2007-05-29
> **flowingfire said:**
> Hi everybody.  I have a problem.  Feisty simply will not boot.  I'll go over what I did and maybe somebody can help.

What caused this problem is this: I installed a second hard drive.  I then proceeded to install Fedora 7 on the new hard drive.  I instructed the Grub bootloader in the Fedora installation to give me options to boot 3 operating systems: Windows Vista, Feisty Fawn, and Fedora 7.  

Now, the bootloader boots the partitions for Windows Vista and Fedora 7 perfectly fine.  What it cannot do is boot Feisty.  I also checked in Windows, and I cannot access the Feisty partition any longer.

Please help if you know what I can do to be able to get my Fesity back.  The name of the partition it is on is sdb2.  I have Grub set to boot sdb2 as Feisty, but it always give me a error.

Thanks,
-David

Post the output of:
```
sudo fdisk -l
```
the -l is a small "L"
if you're doing this from Fedora, you might have to "su", then "fdisk -l"

What you might want to do is write down your entry to boot Fedora 7, then use the Ubuntu live cd to install Ubuntu's grub to the mbr:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

then add the Fedora entry to very end of your Ubuntu /boot/grub/menu.lst.

---

