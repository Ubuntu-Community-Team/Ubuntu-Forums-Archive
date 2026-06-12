---
title: "How to add entry of ubuntu 12.04 live usb partiotion to grub?"
date: 2013-03-25
forum: General Help
---

### Post by chk1827 on 2013-03-25
i have 150 gb external hard disk with following partitions-
/dev/sdb1 elements(data) 123 gb
/dev/sdb2 linuxlivekey(bootable live usb ubuntu 12.04.2) 5gb
/dev/sdb5 /boot
/dev/sdb6 /
/dev/sdb7 /home
/dev/sdb 8 swap

i initially partitioned the disk, installed ubuntu 12.04 live usb in partition 2, then booted the live usb partition and installed ubuntu 12.04...and wrote mbr to /dev/sdb.
but when grub loaded after installing, it displayed entry of ubuntu & windows, but did'nt display the live usb entry.
how can i add entry of the live usb partition to grub so that i can install ubuntu on any other system with my external hdd?

---

### Post by oldfred on 2013-03-25
If you have grub in sdb, you can directly mount the ISO. Or did you extract it?

Does not matter if hard drive, external drive or flash drive. I use this for all of them. It is just getting path and drive number correct as boot drive from BIOS always is hd0.

 This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by chk1827 on 2013-03-26
no i made a live usb partition using linux live usb creator(for windows)..in the partion /dev/sdb2 of 5gb fat32 filesystem..which has persistance of 3.5 gb..which is not present using .iso image...and i want to add entry of this live usb partition to grub...i tried editing the custom grub.d file custom 40 and added 
menuentry 'Ubuntu 12.04.2 LiveUSB'{
set root='(hd1,2)'
chainloader +1
}
but this boots up my windows partition in hd0,2
what to do?

---

### Post by oldfred on 2013-03-26
If you directly boot the flash drive, it will be hd0 and then hard drives are in motherboard port order.
Try set root='hd0,2'
You can test with e on grub menu and edit. That is just a one time change but allows you to experiment. It took me a while to understand how it numbers drives as it is not fixed. Actually it depends on how BIOS reports drives to operating system.

I skipped one port in the middle of my ports and have several drives. Sometimes my flash drive is sdb and others sde. But if I boot it, it is always hd0 in grub, then sda is hd1 for chainloading.

---

### Post by chk1827 on 2013-03-26
That worked!! Thank you :)

---

