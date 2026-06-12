---
title: "Can't reach files from ubuntu partition"
date: 2008-05-12
forum: General Help
---

### Post by Svantevid on 2008-05-12
Hi

I installed ubuntu from windows in a folder on partition I use for storage. Now i can't reach those files, that would be filesystem partition wich is really inconvenient since all my music and videos are there.
And to add a litle off topic to that... I would like to install ubuntustudio, can i install it on that same partition from windows?
Will I lose this ubuntu?

---

### Post by cubeist on 2008-05-12
> **Svantevid said:**
> Hi

I installed ubuntu from windows in a folder on partition I use for storage. Now i can't reach those files, that would be filesystem partition wich is really inconvenient since all my music and videos are there.
And to add a litle off topic to that... I would like to install ubuntustudio, can i install it on that same partition from windows?
Will I lose this ubuntu?

To mount windows partitions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

UbuntuStudio can easily be faked by just installing the applications you want from the repos and then get the ubuntustudio theme... Much easier than re-installing a complete system.  Ubuntu Studio and regular ubuntu are same except for theme and apps.

---

### Post by Svantevid on 2008-05-12
Hey I found this 
[http://onlyubuntu.blogspot.com/2007/03/widows-ntfs-partitions-readwrite.html]("http://onlyubuntu.blogspot.com/2007/03/widows-ntfs-partitions-readwrite.html")

It mounted other partitions with no problem, but when I mounted one with ubuntu on it I got no shortcut or anything?

> UbuntuStudio can easily be faked by just installing the applications you want from the repos and then get the ubuntustudio theme... Much easier than re-installing a complete system. Ubuntu Studio and regular ubuntu are same except for theme and apps.

I heard that the kernel is "more sutable" or whatever in ubuntu studio, to use it for studio purposes, not sure if that's right.

---

### Post by Svantevid on 2008-05-12
I tride folowing waht you sugested and i get this:

> proc /proc proc defaults 0 0
/host/ubuntu/disks/root.disk / ext3 loop,errors=remount-ro 0 1
/host/ubuntu/disks/boot /boot none bind 0 0
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda6 /media/Storage ntfs-3g defaults,locale=en_AU.UTF-8 0 0
/dev/sda5 /media/particija ntfs-3g defaults,locale=en_AU.UTF-8 0 0

I'm suposed to change it, but how?
I need to mount this /dev/sda6...

---

### Post by cubeist on 2008-05-12
> **Svantevid said:**
> Hey I found this 
[http://onlyubuntu.blogspot.com/2007/03/widows-ntfs-partitions-readwrite.html]("http://onlyubuntu.blogspot.com/2007/03/widows-ntfs-partitions-readwrite.html")

I heard that the kernel is "more sutable" or whatever in ubuntu studio, to use it for studio purposes, not sure if that's right.

As far as I know it is the same kernel.

As for mounting windows, I find the easiest way is to make a mount point, then when I want to mount it I do so manually... (you can add it to your fstab like the tutorial suggests too.)

after you have created a mountpoint the command to mount would be:
```
mount -t ntfs /dev/sda6 /path/to/mountpoint
```
then either cd to that directory or navigate there via nautilus.

Also, it is worth the effort to scan through man mount

---

