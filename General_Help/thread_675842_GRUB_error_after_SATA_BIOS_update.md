---
title: "GRUB error after SATA BIOS update"
date: 2008-01-23
forum: General Help
---

### Post by teataster on 2008-01-23
I have a Silicon Image 3112 SATA PCI card and recently updated the BIOS on the controller.

Ubuntu boots from the HD attached to that controller and after the update the GRUB loader hangs.

I tried SuperGRUB and that restored Windows on my IDE HD but doesn't seem able to restore my Ubuntu installation.

The SATA HD shows up under Windows.

I have tried fixing GRUB using the Live CD but the install process hangs just after the section saying that the Partiton Manager is starting.  I think that Ubuntu doesn't like the new BIOS!

Does anyone have any ideas on how I retrieve Ubuntu?

Thanks in advance...

---

### Post by polmir on 2008-01-23
try this link:
[How_To_Use_Super_Grub_Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Use_Super_Grub_Disk")
[Re-install_Grub_with_Live_CD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

---

### Post by teataster on 2008-01-23
Thanks Polmir!  I tried both but with no luck.  If I try to boot GRUB I get the GRUB Loading stage1.5 and then GRUB loading please wait... but nothing else.

SuperGRUB allows me back into Windows but I can't get into Ubuntu.

---

### Post by polmir on 2008-01-24
You start livecd
In terminal
```
fdisk -l /dev/sda
```

sda or sdb or other

---

### Post by teataster on 2008-01-25
Polmir

Thanks for your help.

fdisk l /dev/sda  ->  cannot open /dev/sda
and same for sdb

Only have one SATA disk

D

---

### Post by polmir on 2008-01-25
I am sorry
```
sudo fdisk -l /dev/sda
```

---

### Post by teataster on 2008-01-25
Polmir

Pls don't be sorry, I am grateful for your help.

I should have tried that myself!  Output->

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x65e47c87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       24745   198756180    f  W95 Ext'd (LBA)
/dev/sda5               2       19124   153605466    7  HPFS/NTFS
/dev/sda6           22435       23650     9767488+  83  Linux
/dev/sda7           23651       23772      979933+  82  Linux swap / Solaris
/dev/sda8           23773       24745     7815591   83  Linux

Could it be something to do with the disk id?

---

### Post by polmir on 2008-01-26
type in terminal

```
sudo cfdisk
```

post of out it *(to be careful)*

---

### Post by teataster on 2008-01-26
Ran cfdisk which seemed to only report on sda.  I have a 20GB IDE disk as sda on which I have my original Win2k installation.

I installed Ubuntu on to the new SATA 200GB disk which is 200GB and is sdb.

I looked at both disks under GParted on the LiveCD and Noticed no boot flag on my Ubuntu system partition.  I used 'Manage Flags' to set the boot flag on the correct partition, rebooted and I am back with GRUB hanging.

sdb partitions-
sdb5 NTFS 146.5GB  General data
sdb6 ext3 9.3GB Linux home partition
sdb7 1GB linux swap
sdb8 ext3 7.4GB Linux - now with boot flag set

---

### Post by polmir on 2008-01-26
You read this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153096]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153096")
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153096/+viewstatus]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153096/+viewstatus")

---

### Post by teataster on 2008-01-27
Thanks Polmir- looks like similar issue to mine except that my problem is with the SATA HD on a PCI card rather than a PATA disk.  Issue seems to be with the controller rather than the disk though.

I think the BIOS upgrade on the controller has tripped up on some incompatibility with the 2.6.22-14 linux kernel.

I think I'll give Hardy Heron a go from what the comments say- what do you think?  Do you know if Gutsy is going to update the 2.6.22-14 kernel again?

---

### Post by polmir on 2008-01-27
> **teataster said:**
> ...Do you know if Gutsy is going to update the 2.6.22-14 kernel again? Yes. You have possible to install and compile new kernel.
[http://www.howtoforge.com/kernel_compilation_ubuntu]("http://www.howtoforge.com/kernel_compilation_ubuntu")
[http://www.howtoforge.com/kernel_compilation_debian_etch]("http://www.howtoforge.com/kernel_compilation_debian_etch")
[http://www.kernel.org/]("http://www.kernel.org/")
good luck

<<My Linux is better for my English.>>

---

### Post by teataster on 2008-01-27
Polmir

Your English is much better than my Polish!

Just tried to upgrade the kernel to the Hardy version in Gutsy following this [http://ubuntuforums.org/showthread.php?t=646755]("http://ubuntuforums.org/showthread.php?t=646755"), but still stuck on the 'GRUB loading, please wait.....'  stage.

I'll try to install Alpha3 version of Hardy- if that doesn't work, I will try to downgrade the BIOS version of the SATA controller.

---

### Post by polmir on 2008-01-27
Thanks :)
> **teataster said:**
> 
Just tried to upgrade the kernel to the Hardy version in Gutsy following this [http://ubuntuforums.org/showthread.php?t=646755]("http://ubuntuforums.org/showthread.php?t=646755"), but still stuck on the 'GRUB loading, please wait.....'  stage.

Today I don't know this howto practically.

> 
I'll try to install Alpha3 version of Hardy- if that doesn't work, I will try to downgrade the BIOS version of the SATA controller.

I prefer to You install Ubuntu from alternate Cd.
[https://help.ubuntu.com/community/Installation/I386]("https://help.ubuntu.com/community/Installation/I386")
[https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation")

---

### Post by teataster on 2008-01-27
Bingo!

I downgraded the BIOS on the controller from v4284 to v4250 (I was on 4247 originally) and GRUB now working!

Obviously a hardware problem with the later BIOS version- if I had time I would try the versions in between and work out where the problem started.

Thanks for all your help Polmir!

---

