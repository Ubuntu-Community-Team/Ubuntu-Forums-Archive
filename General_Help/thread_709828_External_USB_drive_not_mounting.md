---
title: "External USB drive not mounting?"
date: 2008-02-27
forum: General Help
---

### Post by Alex&amp;Linux on 2008-02-27
Hello all!
I've spent the last year away from Ubuntu and Linux in general, using  instead OS X on my Intel MacBook.

Ive just installed gutsy, finished updating everything, and I can't seem to get my USB drive to mount properly, The data is quite important, and I'd like to avoid too much trouble getting it to work again.

When I run fdisk -l, I get the following:

```
alex@alex-laptop:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disco /dev/sda: 60.0 GB, 60011642880 bytes
255 cabezas, 63 sectores/pistas, 7296 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0x000065f3

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1        6993    56166016   83  Linux
/dev/sda2   *        6993        7296     2439070+  82  Linux swap / Solaris

Disco /dev/sdb: 320.0 GB, 320072933376 bytes
255 cabezas, 63 sectores/pistas, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0x404b5ca9
Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1       38913   312568641    c  W95 FAT32 (LBA)

```


"/dev/sdb" is my Trekstor 320 GB drive alright, but (and perhaps this is just an amature mistake) I cant "open" it.

It doesnt show in "places", or in the list of devices when I go into the "computer" directy via "places"

Simply put; HOW CAN I READ/WRITE THIS STORAGE VOLUME?

---

### Post by taurus on 2008-02-27
Can you mount it by hand from a terminal?

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

---

### Post by Alex&amp;Linux on 2008-02-27
Well, that seems to have worked rather nicely, and for that you have my sincere thanks!
Now, I wasnt able to dismount "sdb" after we created it, and when reconnecting the device the data would not be accessable, so I had another go at it (this time using "sdc1" as the name) -its working, but I am not sure how to dismount this!

When I attempt to do so, I am given the following error:

"umount: /media/sdc1 is not in the fstab (and you are not root)"

---

### Post by mbsullivan on 2008-02-27
> "umount: /media/sdc1 is not in the fstab (and you are not root)"

You should be able to do it with:

```
sudo umount  /media/sdb1
```

Since you are going to mount this drive regularly, you could always add it to your fstab file (which holds devices which are automatically loaded @ bootup or when "mount -a" is called).

Mike

---

### Post by Alex&amp;Linux on 2008-02-27
Thanks very much Mike!
Cheers!

---

