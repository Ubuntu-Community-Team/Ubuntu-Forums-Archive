---
title: "Can't get into Windows"
date: 2007-06-16
forum: General Help
---

### Post by Kaphix on 2007-06-16
Well, I just seemingly successfully dual booted Vista and Ubuntu; all my files are on the hard drive and the partition is still there. The only problem is, I can't boot into Windows. It automatically loads Ubuntu, and when I press Esc it only lists a bunch of Ubuntu stuff. I tried booting from the hard drive and other things, but it just gets me into Ubuntu.

Heres my Partitions-
[http://i25.photobucket.com/albums/c69/Kaphix/Partitions.png](http://i25.photobucket.com/albums/c69/Kaphix/Partitions.png)

---

### Post by benerivo on 2007-06-17
Can you post the contents of your /etc/fstab file? Thanks.

---

### Post by Kaphix on 2007-07-06
Sorry it took so long.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2 -- converted during upgrade to edgy
UUID=ff087e60-8b42-4fb5-b2cc-eb4de4219a04 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=07D7-0510 /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda3 -- converted during upgrade to edgy
UUID=7C3CBFB23CBF65B4 /media/sda3 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda4 -- converted during upgrade to edgy
UUID=a5b79797-f1f9-4eba-b910-47b346affd6b none swap sw 0 0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by timcredible on 2007-07-06
please list your /boot/grub/menu.lst file (but take out all the commented lines please, the ones with # at the beginning).  you should have something like:

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

either at the beginning or the end.  the line with root (hd0,0) will be differnet for you since your windows partition is not partition 1, your's should be root (hd2,0).  

also, in your screenprint, what's that exclamation point mean by the windows partition?

---

### Post by Kaphix on 2007-07-06
```
title		Ubuntu, kernel 2.6.20-16-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=ff087e60-8b42-4fb5-b2cc-eb4de4219a04 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386
savedefault

title		Ubuntu, kernel 2.6.20-16-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=ff087e60-8b42-4fb5-b2cc-eb4de4219a04 ro single
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=ff087e60-8b42-4fb5-b2cc-eb4de4219a04 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386
savedefault

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=ff087e60-8b42-4fb5-b2cc-eb4de4219a04 ro single
initrd		/boot/initrd.img-2.6.17-11-386

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=ff087e60-8b42-4fb5-b2cc-eb4de4219a04 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=ff087e60-8b42-4fb5-b2cc-eb4de4219a04 ro single
initrd		/boot/initrd.img-2.6.15-28-386

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=ff087e60-8b42-4fb5-b2cc-eb4de4219a04 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=ff087e60-8b42-4fb5-b2cc-eb4de4219a04 ro single
initrd		/boot/initrd.img-2.6.15-26-386

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
```

And the exclamation says it can't find mountpoint.

Oh man, I thank you so much.
I added the line you said, except with "hda0,2", and now I can boot into Vista.

---

