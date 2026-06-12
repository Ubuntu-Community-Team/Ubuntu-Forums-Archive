---
title: "Desparate for help: cannot boot linux partitio (GRUB error 17), superblock trouble?"
date: 2007-09-25
forum: General Help
---

### Post by kwilliam on 2007-09-25
Ok, so this is probably the strangest story you ever heard.  I use a laptop, dual booting Windows Vista and Kubuntu Linux.  Wanting to free up some room on my hard drive, I booted Vista and tried to delete the Dell Recovery partition, since I have the Vista backup CD, and I don't need that partition really.  I rebooted, and all hell had broken loose!

Grub gave an Error 22.  I booted from the Ubuntu Live CD, opened GParted to discover that Vista had deleted my linux (ext3) partitions (root and home)!  I managed to recover them with TestDisk (sudo apt-get install testdisk), but TestDisk screwed up my Vista installation; it didn't recognize the NTFS partitions and globbed them into a FAT32 partition when it rewrote the partition table.  I could now mount my Linux partitions and recover my files, but try as I might, I could not boot them.  I managed to restore GRUB, but now I get an "Error 17: Cannot mount selected partition" when I try to boot Linux.  (Trying to boot Vista gets an "Error 12: Invalid device requested" which makes sense since the NTFS partition isn't in the partition table anymore.  I'm less worried about Vista.)

I tried to run fsck from the Live CD, but get this error:
```
ubuntu@ubuntu:~$ sudo fsck /dev/hda
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext2: No such file or directory while trying to open /dev/hda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo fsck -r /dev/hda
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext2: No such file or directory while trying to open /dev/hda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

I even used parted to set the boot flag for my ext3 partition.
```
(parted) print                                                            

Disk /dev/sda: 100GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  57.6MB  57.5MB  primary   fat16             
 2      57.6MB  34.4GB  34.4GB  primary   fat32        lba  
 3      55.5GB  97.9GB  42.4GB  extended               lba  
 5      55.5GB  75.9GB  20.5GB  logical   ext3         boot 
 6      75.9GB  95.4GB  19.5GB  logical   ext3              
 7      95.4GB  97.9GB  2476MB  logical   linux-swap 
```

**Anybody know how to make my Linux installation boot again?**

---

### Post by kwilliam on 2007-09-25
Ah, quick note: it should have been /dev/sda, not /dev/hda:
```

ubuntu@ubuntu:~$ sudo fsck /dev/sda
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

---

### Post by jamvegan on 2007-09-25
One thing that I notice is that you were trying to run fsck on /dev/hda, but parted identifies the drive as /dev/sda.

Have you tried manually editing Ubuntu's grub entry at boot time (by highlighting the entry and typing "e")?  In particular the root line and the root portion of the kernel line?  I've seen others who are experiencing error 17 have success with changing the UUID to a logical name, for instance:
```
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=b497a47a-fd39-41e1-8774-ab4dd239d2f1 ro quiet splash
```
to:
```
kernel          /boot/vmlinuz-2.6.20-16-generic root=/dev/sda5 ro quiet splash
```

Best of luck to you. :-)

---

### Post by kwilliam on 2007-09-26
Hey I fixed it!  The problem was in GRUB, but not in the UUID.  When Vista deleted the Dell Recovery partition and TestDisk combined two NTFS partitions into one FAT partition, the grub name of my root partition changed from (hd0,6) to (hd0,4).  Makes sense.

---

