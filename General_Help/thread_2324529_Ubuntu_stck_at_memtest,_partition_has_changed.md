---
title: "Ubuntu stck at memtest, partition has changed"
date: 2016-05-14
forum: General Help
---

### Post by Yoav_T_L on 2016-05-14
Hi all, 
Don't know how it happened, but after some update and upgrade my computer stuck on memtest. 
now i followed this thread - [http://ubuntuforums.org/showthread.php?t=1679879](http://ubuntuforums.org/showthread.php?t=1679879) 
but i had the problem here- 
when running gparted -l this is the output 
```

Model: ATA ST500LT012-9WS14 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   500GB  500GB  extended
 5      257MB   500GB  500GB  logical                lvm
```

so when i mount 
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys 

there is nothing. 

the boot partiton have only this file on it 
drwxr-xr-x 5 root root   1024 May  8 08:14 grub
drwx------ 2 root root  12288 Aug 10  2014 lost+found
-rw-r--r-- 1 root root 182704 Aug 27  2015 memtest86+.bin
-rw-r--r-- 1 root root 184380 Aug 27  2015 memtest86+.elf
-rw-r--r-- 1 root root 184840 Aug 27  2015 memtest86+_multiboot.bin

 
how do i fix it without ruining my entire files?

---

