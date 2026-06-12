---
title: "must mount ext3 every time."
date: 2007-01-07
forum: General Help
---

### Post by hostage on 2007-01-07
Hello.
i have a irritating problem, i formatted my NTFS to EXT3, and i have read many threads about "mounting ext3" but i have not find the answere to this.

my problem is that i have to mount the disk every time i log in to the system, then i write this in the terminal: "sudo mount -t ext3 /dev/sda5 /media/sda5" to mount the disk, then it work, but when i want to start the computer again i have to mount it all over again :( ??????!!!!!!!!

this is my fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=952c84bd-90c1-49ac-babc-906476375552 /               ext3    defaults,errors=remount-ro 0       1
[B]# /dev/sda5
UUID=0E6CD7F26CD7D297 /media/sda5     ext3    defaults,rw 0       0[/B]
# /dev/sdb5
UUID=10140E02140DEC12 /media/sdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

---

### Post by Ramses de Norre on 2007-01-07
Are you sure the UUID is correct? What happens if you umount it and then run **sudo mount -a** ?
Is it listed when you do **mount** before mounting it manually?

The line looks correct to me so this is rather strange..

---

### Post by mcduck on 2007-01-07
If you formatted the partition then the UUID has changed.

Check the new UUID with 'ls /dev/disk/by-uuid -alh' and change the value in fstab :)

---

### Post by hostage on 2007-01-07
No im not sure if the UUID is right... because i didn't changed the UUID. 
I dont know how to unmount it. I tried to unmount it in GPARTED but i can't ?!

And when i Listed the UUID, this came up

drwxr-xr-x 2 root root 120 2007-01-07 12:35 .
drwxr-xr-x 6 root root 120 2007-01-07 12:27 ..
lrwxrwxrwx 1 root root  10 2007-01-07 12:27 10140E02140DEC12 -> ../../sdb5
lrwxrwxrwx 1 root root  10 2007-01-07 12:27 952c84bd-90c1-49ac-babc-906476375552 -> ../../sda3
**lrwxrwxrwx 1 root root  10 2007-01-07 12:35 a20cd95c-99ea-49ed-b155-bd2a27b3c314 -> ../../sda5**
lrwxrwxrwx 1 root root  10 2007-01-07 12:27 f38afb69-f654-4cd7-8c14-a8752be2bf14 -> ../../sda1

And the UUID that camed up seemed to be much much longer then the original so i don't know if that is the right UUID?!

maybe this is the new UUID? "bd2a27b3c314"

---

### Post by hostage on 2007-01-07
thanks mcduck and ramses. 

i just changed the uuid in the fstab, saved it and restarted the computer
it worked :D thanks very much.. now i have learned some good stuff in ubunut.
im very new, only used ubuntu in 2 months, had windows xp before,  but windows suck!

:D:D:D:D:D

---

### Post by mcduck on 2007-01-07
Ok, the right entry for your fstab is this:
```
# /dev/sda5
UUID=a20cd95c-99ea-49ed-b155-bd2a27b3c314 /media/sda5 ext3 defaults,rw 0 0
```

edit: too slow, but it's good you got it working :)

---

### Post by hostage on 2007-01-07
well i have one problem left i see.. when i look in GPARTED, according to gparted i should have 160 gb but when i look att properties at the sda5 disk it says i only have 150gb.. that strange because i know i had 160gb when it was NTFS! 10 gb can't just disappear just like that?!

---

### Post by mcduck on 2007-01-07
5% of disk space is reserved for root only (and is not visible to normal users), and also journaling in Ext3 takes some space.

As that partition is not used for /, you could safely set all disk space available to users on that partition with this command: 'sudo tune2fs -r 0 /dev/sda5'

---

