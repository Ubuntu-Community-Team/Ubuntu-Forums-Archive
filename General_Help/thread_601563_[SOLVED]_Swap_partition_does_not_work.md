---
title: "[SOLVED] Swap partition does not work"
date: 2007-11-03
forum: General Help
---

### Post by AsoSako on 2007-11-03
Hello.  I just installed Gusty and I have noticed that my Swap partition never works at all.  I don't think it is supposed to be that way since I only have 1gig of RAM and when I use it at 90+% my Swap partition is still at 0% use.

Here is my /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=87f31df6-3e10-4598-bc90-22fdb8488b3b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=F407-D4AF  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=4f3e5318-eb03-4cdc-b817-173398e673b0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

Please help I want my swap partition to be functional.

---

### Post by mrvertigo on 2007-11-03
I will look into this

---

### Post by Happy_Man on 2007-11-03
Please post the ouput of the command ```
sudo fdisk -l
``` Whatever partition is labeled as "Solaris/linux swap", enter in this command: ```
sudo swapon <name of partition>
``` If you can't find a partition thus labeled, it means you don't have a swap partition on your HDD.

---

### Post by taurus on 2007-11-03
What's the output of this command from a terminal then?

```
free
```

---

### Post by AsoSako on 2007-11-03
Output of sudo fdisk -l
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf7d8f7d8
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+   c  W95 FAT32 (LBA)
/dev/sda2            3265        3656     3148740   82  Linux swap / Solaris
/dev/sda3            3657       30401   214829212+  83  Linux
```

After sudo swapon sda2
```
agsimeonov@agsimeonov-linux:~$ sudo swapon sda2
swapon: cannot stat sda2: No such file or directory
```

Output of free
```
             total       used       free     shared    buffers     cached
Mem:       1035324    1017600      17724          0      13260     670240
-/+ buffers/cache:     334100     701224
Swap:      3148732          0    3148732
```

---

### Post by AsoSako on 2007-11-03
Sudo swapon sda2 basically does not work...

---

### Post by chunderbunny on 2007-11-03
The command should be "sudo swapon /dev/sda2" but that's not the problem here. According to *free* you're only using 300MB of memory, so it's no surprise that swap isn't being used. Please see here:
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)
for more details.

---

