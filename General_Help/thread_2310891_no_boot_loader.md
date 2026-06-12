---
title: "no boot loader"
date: 2016-01-22
forum: General Help
---

### Post by jrosen2 on 2016-01-22
Everything was running fine - i have a dual boot (win 10 & Ubuntu). Last night after a restart it comes up with no OS instead of my normal bootloader screen.  I boot from a live CD and ran through the GRUB2 boot repair, but it didnt fix anything.  The output is here [http://paste.ubuntu.com/14061732](http://paste.ubuntu.com/14061732).  I hoping I can get this working without having to start all over..not sure where to go next..
TIA,
Jeff

---

### Post by yancek on 2016-01-22
The link you posted is not from boot repair and shows nothing about your computer drives/partitions or boot files.  Run the boot repair again and read through the instructions.  I don't know what you did but there should not be any information on Minecraft games in a boot repair output.

---

### Post by jrosen2 on 2016-01-22
[http://paste.ubuntu.com/14601732/](http://paste.ubuntu.com/14601732/) ... fat fingered it

gparted shows
/dev/sde (931.51 GiB)
/dev/sde1 fat32 190 MiB boot
/dev/sde2 ext2 244 MiB msftdata
/dev/sde3 lvm2 pv 931 GiB lvm

/dev/sdf
/dev/sdf1 unknown 128 MiB msftres
/dev/sdf2 ntfs 1.82 TiB msftdata
/dev/sdf3 ntfs 450 MiB hidden,diag

---

### Post by oldfred on 2016-01-23
What is sdf? 
Script is not showing it at all.

You did a full drive LVM install on sde. That then has no Windows. 
So was Windows on another drive?

There seems to be some corruption on the ESP - efi system partition on sde1. Either chkdsk from Windows or fsck from Ubuntu. 

Not sure which works or works better:sudo /sbin/fsck.vfat -V <the fat32 device>
 sudo fsck.vfat -t -a /dev/sde1
man dosfsck
or

 dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sde1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

