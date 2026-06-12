---
title: "Automatically mounting secondary harddrive at start-up"
date: 2007-10-03
forum: General Help
---

### Post by j.miller565 on 2007-10-03
I'm just wondering how to automatically mount my secondary harddrive (sdb1) (30 GB hard drive) when I start Ubuntu.  
BTW, I use my second drive for video podcasts off Miro.  


Cheers,
j.miller565

---

### Post by taurus on 2007-10-03
You can mount it automatically each time you boot ubuntu by addning an entry in /etc/fstab for it.  What filesystem is it anyway?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by j.miller565 on 2007-10-03
Well sdb1 is formatted as ext3
```
simon@green-kubuntu-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3965    31848831    c  W95 FAT32 (LBA)
/dev/sda2            3966        8002    32427202+  83  Linux
/dev/sda3            9542        9729     1510110    5  Extended
/dev/sda4            8003        9537    12329887+   7  HPFS/NTFS
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 33.8 GB, 33820286976 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4111    33021576   83  Linux
```

---

### Post by strabes on 2007-10-04
You could add a line into your fstab similar to this:> /dev/sdb2 /media/videopodcasts ext3 defaults 0 2I'm not sure if you have to make the directory. Try without making it. If you do, run this command to make the directory: ```
sudo mkdir /media/videopodcasts
```Then you have to set the proper permissions:```
sudo chown YOURUSERNAME:YOURUSERNAME /media/videopodcasts && sudo chmod 655 -R /media/videopodcasts
```

I'm not 100% sure on the permissions numbers. Somebody please correct me if they should be something else.

---

### Post by j.miller565 on 2007-10-04
cheers thanks strabes, I'm going to try it right after I finish compiling the new kernel(6.22.9) :)

Thanks strabes

---

### Post by chronotrigger on 2008-02-25
Taurus and strabes, thanks for the help, much appreciated.

---

