---
title: "Help!"
date: 2007-08-26
forum: General Help
---

### Post by ashvala on 2007-08-26
I use Debian etch & there is a certain problem that i face,

I try to mount /cdrom & then it says
bash:/dev/hdd doesn't exist

And in /etc/fstab:
/etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
/dev/hde3 / ext3 errors=remount-ro 0 1
/dev/hde2 none swap sw 0 0
proc /proc proc defaults 0 0
/dev/fd0 /floppy auto user,noauto,exec 0 0
/dev/hdd /cdrom iso9660 ro,user,noauto,exec 0 0
/dev/hdc /cdwriter iso9660 ro,user,noauto,exec 0 0
/dev/hde5 /usr ext3 defaults 0 2
/dev/hde6 /home ext3 defaults 0 2
/dev/hde7 /var ext3 defaults 0 2
/dev/hde8 /work ext3 defaults 0 2
# /dev/hdb8 /oldroot ext3 defaults 0 2
# /dev/hdb6 /oldhome ext3 defaults 0 2
/dev/sdb1 /usb auto user,noauto,exec 0 0
/dev/sdb2 /ipod vfat user,noauto,exec 0 0
/dev/hde1 /win vfat user,noauto,exec 0 0
/dev/sda1 /new1 auto defaults 0 0
/dev/sda2 /new2 ext3 defaults 0 0
/dev/sda3 /new3 ext3 defaults 0 0


Can anyone help me?

---

### Post by jamvegan on 2007-08-26
Do you have both a CD-ROM and a CD-RW drive installed?  Two separate drives?  Because that is what your /etc/fstab seems to indicate.  If so, try running:
```
sudo lshw
```
and find the section that starts with *-cdrom.  Does it show that the logical name is /dev/hdd (which is what you have in fstab), or something else?

---

### Post by ashvala on 2007-08-27
Well... 
* I ain't  a sudoer on the PC

*Whenever I try to mount, It tells bash:/dev/hdd special device doesn't exist.

*Any help?

---

### Post by jamvegan on 2007-08-27
Are you able to mount and/or use /cdwriter?

---

### Post by ashvala on 2007-08-30
Nothing....
I am not able to mount either of the to cd drives & the usb & ipod

---

