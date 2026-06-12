---
title: "HD and Grub issues with mount"
date: 2007-03-28
forum: General Help
---

### Post by siucdude on 2007-03-28
Well maybe you can help me, I got a big and almost no problem but playing with it for few days I figured I ask. I have two HD sda1 is my / and sdb1 is other HDD,

I followed you instructions to mount and show other HD and it worked but when I ran df -h I got this

siucdude@tomasz-laptop:~$ df -h
Filesystem Size Used Avail Use% Mounted on
varrun 506M 88K 506M 1% /var/run
varlock 506M 0 506M 0% /var/lock
procbususb 10M 140K 9.9M 2% /proc/bus/usb
udev 10M 140K 9.9M 2% /dev
devshm 506M 0 506M 0% /dev/shm
lrm 506M 18M 489M 4% /lib/modules/2.6.17-11-generic/volatile
/dev/sdb1 74G 181M 70G 1% /media/sdb1


as you may see it show the second HD but no root

I checked my gparted to where its mounted and looks different then my other pc.
it says /dev/sda1 ext3 mountpoint= /, /dev/.static/dev

Below are some other outputs i came accross.

siucdude@tomasz-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 9356 75152038+ 83 Linux
/dev/sda2 9357 9733 3028252+ 5 Extended
/dev/sda5 9357 9733 3028221 82 Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 1 9729 78148161 83 Linux

and

siucdude@tomasz-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=1034dfd9-f59b-4ace-995a-d20186fff841 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=403c105c-5a1d-473d-a739-c5dff4f0b5ba none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
#second HDD
/dev/sdb1 /media/sdb1 ext3 defaults 0 1


Hope this all helps, Please let me know,

One more thing after I installed Ubuntu(not dual boot) I noticed that Grub wanted to boot fom /dev/hda1, so I chnage it everytime I boot at grub.

Thanks
TJ

---

