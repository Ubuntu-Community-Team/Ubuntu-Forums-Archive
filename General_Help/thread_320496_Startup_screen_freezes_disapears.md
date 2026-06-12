---
title: "Startup screen freezes disapears"
date: 2006-12-17
forum: General Help
---

### Post by glendavee on 2006-12-17
I'm a newbie with Edgy. For the first few days, ubuntu booted up quickly, with the startup screen status bar scrolling nicely across the screen. Recently the status bar stalls halfway across the screen and then this screen disappears and text appears as follows:
activating swap                             (fail)
checking root file system             (ok)
checking file systems                    (ok)

This hangs around for about 1 minute then the signon screen appears.
Its annoying, but not really serious - any suggestions on how to fix this??

---

### Post by taurus on 2006-12-17
Boot into recovery mode from GRUB menu and paste the output of these two commands here...

```
fdisk -l
cat /etc/fstab
```

---

### Post by glendavee on 2006-12-17
Here it is :

david@david-desktop:~$ fdisk -l

Disk /dev/sdc: 252 MB, 252416000 bytes
53 heads, 32 sectors/track, 290 cylinders
Units = cylinders of 1696 * 512 = 868352 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         291      246384    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(7, 52, 32) logical=(290, 29, 32)
david@david-desktop:~$ cat/etc/fstab
bash: cat/etc/fstab: No such file or directory
david@david-desktop:~$

---

### Post by taurus on 2006-12-17
There should be a space between "cat" and "/etc/fstab"...

```
cat        /etc/fstab
```
You only have one harddrive, SATA!!!  Try to run it with the sudo in front.

```
sudo fdisk -l
```

---

### Post by glendavee on 2006-12-17
Sorry, here's another try (I do have 2 hard disks)
david@david-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       19060   153051255    7  HPFS/NTFS
/dev/sda3           19061       19452     3148740   db  CP/M / CTOS / ...

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30027   241191846   83  Linux
/dev/sdb2           30028       30401     3004155    5  Extended
/dev/sdb5           30028       30401     3004123+  82  Linux swap / Solaris

Disk /dev/sdc: 252 MB, 252416000 bytes
53 heads, 32 sectors/track, 290 cylinders
Units = cylinders of 1696 * 512 = 868352 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         291      246384    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(7, 52, 32) logical=(290, 29, 32)
david@david-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sdb1
UUID=d32be766-a3a3-4717-bab6-b2a123b2e9ec  /              ext3         defaults,errors=remount-ro  0  1  
# /dev/sdb5
UUID=22f2954b-7b2e-40a1-8955-99e60e6bd4fd  none           swap         sw                          0  0  
/dev/hda                                   /media/cdrom0  udf,iso9660  user,noauto                 0  0  
/dev/sda2                                  /media/sda2    ntfs         nls=iso8859-1,umask=000,ro  0  0  
/dev/sdc1                                  /media/sdc1    vfat         defaults                    0  0  
/dev/sdb1                                  /media/sdb1    ext3         defaults                    0  0  
/dev/sdb5                                  /media/sdb5    swap         defaults                    0  0  
/dev/sda1                                  /media/sda1    vfat         defaults                    0  0  
/dev/sda2                                  /media/sda2    ntfs         defaults                    0  0  
/dev/sda3                                  /media/sda3    vfat         defaults                    0  0

---

### Post by taurus on 2006-12-17
The entry for swap partition is wrong in /etc/fstab.  You need to remove the old one, /dev/sdb5, and add the new one it for it...

old:
```

/dev/sdb5   /media/sdb5  swap   defaults   0   0 

```

new:
```

/dev/sdb5   none   swap   sw   0   0

```

---

### Post by glendavee on 2006-12-17
Thanks. How do I do this? Can I just edit the output of cat /etc/fstab?

---

### Post by taurus on 2006-12-17
You need to open an editor and edit /etc/fstab.  

Applications -> Accessories -> Terminal
```
gksudo  gedit  /etc/fstab
```

---

### Post by glendavee on 2006-12-17
Made the change, but it hasn't made any difference to the startup.

---

### Post by taurus on 2006-12-17
Can you paste the output of these two commands here?

Applications -> Accessories -> Terminal
```
cat  /etc/fstab
free
```

---

### Post by glendavee on 2006-12-17
david@david-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sdb1
UUID=d32be766-a3a3-4717-bab6-b2a123b2e9ec  /              ext3         defaults,errors=remount-ro  0  1  
# /dev/sdb5
UUID=22f2954b-7b2e-40a1-8955-99e60e6bd4fd  none           swap         sw                          0  0  
/dev/hda                                   /media/cdrom0  udf,iso9660  user,noauto                 0  0  
/dev/sda2                                  /media/sda2    ntfs         nls=iso8859-1,umask=000,ro  0  0  
/dev/sdc1                                  /media/sdc1    vfat         defaults                    0  0  
/dev/sdb1                                  /media/sdb1    ext3         defaults                    0  0  
/dev/sdb5                                  /media/sdb5    swap         sw                    0  0  
/dev/sda1                                  /media/sda1    vfat         defaults                    0  0  
/dev/sda2                                  /media/sda2    ntfs         defaults                    0  0  
/dev/sda3                                  /media/sda3    vfat         defaults                    0  0  
david@david-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:       1026064     363632     662432          0       8860     162840
-/+ buffers/cache:     191932     834132
Swap:      3004112          0    3004112

---

### Post by taurus on 2006-12-17
Okay, let's try this again.  The entry for /dev/sdb5, is still wrong!!!

old (wrong):
```
/dev/sdb5   **/media/sdb5**   swap   sw   0   0 
```

new:
```
/dev/sdb5   **none**   swap   sw   0   0
```
So please change it with "gksudo gedit /etc/fstab" and reboot...

p.s.  Wait, your swap partition is already mounted in /etc/fstab!!!

```

UUID=22f2954b-7b2e-40a1-8955-99e60e6bd4fd none swap sw 0 0 

```
You don't need another entry for /dev/sdb5 then...

---

### Post by glendavee on 2006-12-17
Still no joy. Same sequence on startup
current output of /etc/fstab
david@david-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sdb1
UUID=d32be766-a3a3-4717-bab6-b2a123b2e9ec  /              ext3         defaults,errors=remount-ro  0  1  
# /dev/sdb5
UUID=22f2954b-7b2e-40a1-8955-99e60e6bd4fd  none           swap         sw                          0  0  
/dev/hda                                   /media/cdrom0  udf,iso9660  user,noauto                 0  0  
/dev/sda2                                  /media/sda2    ntfs         nls=iso8859-1,umask=000,ro  0  0  
/dev/sdc1                                  /media/sdc1    vfat         defaults                    0  0  
/dev/sdb1                                  /media/sdb1    ext3         defaults                    0  0  
/dev/sdb5                                  none    swap         sw                    0  0  
/dev/sda1                                  /media/sda1    vfat         defaults                    0  0  
/dev/sda2                                  /media/sda2    ntfs         defaults                    0  0  
/dev/sda3                                  /media/sda3    vfat         defaults                    0  0

---

### Post by taurus on 2006-12-17
Why don't you edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and remove these two lines from it.

```

# /dev/sdb5
UUID=22f2954b-7b2e-40a1-8955-99e60e6bd4fd none swap sw 0 0 

```
Save it and reboot...

p.s.  I can see there are some minor problems with your /etc/fstab regarding 
```

/dev/sdc1 /media/sdc1 vfat defaults 0 0
/dev/sdb1 /media/sdb1 ext3 defaults 0 0
/dev/sda1 /media/sda1 vfat defaults 0 0
/dev/sda2 /media/sda2 ntfs defaults 0 0
/dev/sda3 /media/sda3 vfat defaults 0 0

```

---

### Post by glendavee on 2006-12-17
Done that. Status bar screen still gives up halfway, but now "activating swap" result is (OK)
Still hangs for about 1 minute on "checking file systems.........................(ok) fsck 1.39

---

### Post by MarkRobert on 2006-12-20
I have the same problem, hangs on boot with same message. Will check out my fstab later.

---

