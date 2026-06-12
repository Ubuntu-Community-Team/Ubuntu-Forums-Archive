---
title: "grub error 17 partition mess up"
date: 2007-01-03
forum: General Help
---

### Post by ygong on 2007-01-03
I cannot start up my laptop, the error message is
Loading grub, stage 1.5
Grub loading, please wait .....
Error 17

the results of fdisk -l are
---------------------------------
Disk /dev/hda: 80.0GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
units=cylinders of 16065*512=8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 5100 40965718+ 7 HPFS/NTFS
/dev/hda2 5100 9729 37187609 f W95 Ext'd (LBA)
Partition 2 does not end on cylinder bounday
/dev/hda5 5100 7257 17331741 83 Linux
/dev/hda6 * 7258 8852 12811806 83 Linux
/dev/hda7 8853 8924 578308+ 82 Linux swap/Sloaris
/dev/hda8 8925 9186 2101648+ 82 Linux swap/Solaris
/dev/hda9 9186 9729 4362088+ b W95 FAT32

I installed windows xp in hda1, a windows/linux shared partition in hda9, originally redhat was installed in hda5, then I wanted to try ubuntu and the partitition split hda5 to hda5 and hda6, ubuntu is installed in hda6. I don't know why hda2 was there and I messed up with the strat and end blocks.

---------------------------------------
Results of cat /boot/grub/device.map:
(hd0) /dev/hda
------------------------------
menu.lst:
default 0
timeout 10
title Ubuntu, kernel 2.6.17-10-generic
root (hd0,7)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda8 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,7)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda8 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,7)
kernel /boot/memtest86+.bin
quiet
boot

--------------
I tried to use live cd to boot the laptop, but gparted does not recognize the hard disk, so I cannot do any partition by using gparted or cfdisk. When I entered grub and typed root + tab, then I get the error message:
error 1: filename must be either an absolute pathname or blocklist

I am kind of new in linux system, some experts out there please help me fix my problem.
thanks a lot

---

### Post by ubuntu27 on 2007-01-03
**bump**

---

### Post by ygong on 2007-01-04
Nobody out there can help me fix the partition problem? Really need help.

---

### Post by bodhi.zazen on 2007-01-04
Try editing /boot/grub/menu.lst and change the enteries 

root (hd0,7)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda8 ro quiet splash

to

root (hd0,5)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro quiet splash

---

### Post by ygong on 2007-01-04
I don't think the grub loads the menu.lst file, the problem should not be in that file and it should be the partition problem. When I used live cd boot up, the hard drive cannot be seen from command although I can mount it. Also gparted does not know the partition.

---

### Post by Bigbluecat on 2007-01-04
You probably need to re-install grub to your MBR. This first part of grub points to the location of your menu.lst. Since you changed the partitions it is probably pointing to the wrong place.

You can do this from the live CD.

---

### Post by bodhi.zazen on 2007-01-04
17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

Your current menu.lst points to swap. You must direct it to your Ubuntu root partition.

> When I used live cd boot up, the hard drive cannot be seen from command although I can mount it.

Not following you here ....

> Also gparted does not know the partition.

Not following you here either ....

---

### Post by ygong on 2007-01-04
I am currently backing up my hard drive, I will try your method later.  When I entered grub typed root + tab, then I get the error message:
error 1: filename must be either an absolute pathname or blocklist
I can mount /dev/hda6. 
When I used gparted, it gives no partition except says that my hard drive is unallocated.

---

### Post by bodhi.zazen on 2007-01-04
Hmmmm ....

Your partition table looks odd ....

It looks like you have two swap partitions.

And which one is Ubutnu root ?

Have you been moving/reformatting/resizing ?

---

### Post by ygong on 2007-01-04
I tried to change to 
root (hd0,5)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro quiet splash
and it didn't work.
/dev/hda6 is the ubuntu root. /dev/hda5 is supposed to be redhat linux and I tried to format that partition /dev/hda5, but it seemed didn't work.
thanks for your help

---

