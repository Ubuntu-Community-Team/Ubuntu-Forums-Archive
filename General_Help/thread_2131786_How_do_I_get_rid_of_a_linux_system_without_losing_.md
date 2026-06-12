---
title: "How do I get rid of a linux system without losing the boot for the others?"
date: 2013-04-02
forum: General Help
---

### Post by gotnexusbluz on 2013-04-02
I have Windows 7, Xubuntu, and I thought I would try Edubuntu as well. Now I've decided to stick with Xfce, but Edubuntu has made itself the default system to boot. If I just delete the Edubuntu partition, will this brick my laptop? I suspect it will, and I am wondering what software is good for reconfiguring my boot record, and how it could be used.

---

### Post by papibe on 2013-04-02
Hi gotnexusbluz.

I'd recommend taking a look at [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). It is usually used from a Live media.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Moose on 2013-04-02
I'll have a go at explaining what pabibe left out. You can't uninstall a Linux system without harming the boot sequence. You will need to fix the boot sequence some way or another after you delete the Linux system. (Using third party software like pabibe mentioned.) If you have a copy of Windows XP lying around you can use the CD to fix the boot, or if you don't you can just search google for a boot-repair bootable iso. (Or something along the lines of that.)

---

### Post by deadflowr on 2013-04-02
Could you post the results of

```
sudo fdisk -l
```
(That's a small L)

This will tell us where everything is, in terms of what partitions are set to boot.

---

### Post by gotnexusbluz on 2013-04-02
> **deadflowr said:**
> Could you post the results of

```
sudo fdisk -l
```
(That's a small L)

This will tell us where everything is, in terms of what partitions are set to boot.
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c31f6


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488508799   244254368+   7  HPFS/NTFS/exFAT
/dev/sda3       488509438   976771071   244130817    5  Extended
/dev/sda5       968962048   976771071     3904512   82  Linux swap / Solaris
/dev/sda6       488509440   586165689    48828125   83  Linux
/dev/sda7       586166272   683821055    48827392   83  Linux
/dev/sda8       683823104   781477887    48827392   83  Linux
/dev/sda9       781479936   968959999    93740032   83  Linux


Partition table entries are not in disk order


Disk /dev/mapper/cryptswap1: 3998 MB, 3998220288 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7809024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x22589431


Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

---

### Post by layers on 2013-04-02
another vote for boot repair !!!!

---

### Post by Wim Sturkenboom on 2013-04-03
My approach would be to boot into Xubuntu and run the command below.
```

sudo update-grub

```
This will update grub with the information from the Xubuntu install; it will still pick up the edubuntu install and add that as an option to the menu.
Next reboot to see if you can get into Xubuntu and Windows without problems. If it works, remove the Edubuntu partition from Windows or Xubuntu, run the above command again in Xubuntu and you should have achieved what you wanted.

As said, that is how I would do it.

And a note: fiddling with disks is always a little risky; user mistakes, power failures, ... I therefore strongly suggest that you have up-to-date backups of anything that is valuable to you, whichever approach you use.

---

### Post by nerdtron on 2013-04-03
> **gotnexusbluz said:**
> I have Windows 7, Xubuntu, and I thought I would try Edubuntu as well. Now I've decided to stick with Xfce, but Edubuntu has made itself the default system to boot. If I just delete the Edubuntu partition, will this brick my laptop? I suspect it will, and I am wondering what software is good for reconfiguring my boot record, and how it could be used.

Here's what I would do:
Boot into Xubuntu, and run on the terminal
```
sudo grub-install /dev/sda
```
Assuming sda is your first hard drive, this command will install Xubuntu's GRUB and will takeover the boot process. Then run
```
sudo update-grub
```
This is make sure that GRUB will scan all avail operating systems. You can now delete the Edubuntu partition. Run update-grub again to remove the entry for Edubuntu.

---

