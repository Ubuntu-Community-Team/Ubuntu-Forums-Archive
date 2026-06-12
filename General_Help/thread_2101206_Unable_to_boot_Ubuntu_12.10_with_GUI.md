---
title: "Unable to boot Ubuntu 12.10 with GUI"
date: 2013-01-04
forum: General Help
---

### Post by erik1001 on 2013-01-04
Ubuntu 12.10 64 bit shows"An error occurred while mounting /mnt/$UUID" on boot screen. If I press S to skip it, it shows me command line interface and if I try to switch to GUI with Ctrl+Alt+F7, it shows me blank black screen.

Partitions on my internal HDD are:

NTFS for Windows
ext4 for /
ext4 for /var
ext4 for /home
swap
When I'm in command line and type ls /home or ls /var it returns nothing, so obviously they are not mounted. What is more, I tried mount /dev/sda7 /var but it asked me for filesystem and because I wasn't sure I gave it up.

Now I'm writing from my Ubuntu 12.04 on USB HDD and the same partitions mount properly.

Thanks in advance.

---

### Post by fdrake on 2013-01-04
> **erik1001 said:**
> Ubuntu 12.10 64 bit shows"An error occurred while mounting /mnt/$UUID" on boot screen. If I press S to skip it, it shows me command line interface and if I try to switch to GUI with Ctrl+Alt+F7, it shows me blank black screen.

Partitions on my internal HDD are:

NTFS for Windows
ext4 for /
ext4 for /var
ext4 for /home
swap
When I'm in command line and type ls /home or ls /var it returns nothing, so obviously they are not mounted. What is more, I tried mount /dev/sda7 /var but it asked me for filesystem and because I wasn't sure I gave it up.

Now I'm writing from my Ubuntu 12.04 on USB HDD and the same partitions mount properly.

Thanks in advance.

post the output of :

```

sudo fdisk -l
sudo blkid
less /etc/fstab

```

---

### Post by erik1001 on 2013-01-04
Because I'm running my portable Ubuntu, these are the results only for the internal HDD:
```
user@home-PC:~$ sudo fdisk -l
[sudo] password for user: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000a88d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   614402047   306841600    7  HPFS/NTFS/exFAT
/dev/sda3       614404094  1952292863   668944385    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       614404096   682761517    34178711   83  Linux
/dev/sda6       682764288   692527103     4881408   82  Linux swap / Solaris
/dev/sda7       692529152   790183935    48827392   83  Linux
/dev/sda8       790185984  1952292863   581053440   83  Linux

```


```
user@home-PC:~$ sudo blkid
[sudo] password for user: 
/dev/sda1: LABEL="System Reserved" UUID="F692E6D892E69BFD" TYPE="ntfs" 
/dev/sda2: UUID="84E000A7E000A212" TYPE="ntfs" 
/dev/sda5: UUID="ea7728c0-d5fe-4914-a93a-5e089ca7ea1d" TYPE="ext4" 
/dev/sda6: UUID="47af9af9-cd50-4d79-882e-e6311a0fd780" TYPE="swap" 
/dev/sda7: UUID="ab8cddf2-84c4-4f09-a94b-3e29e2b32e8d" TYPE="ext4" 
/dev/sda8: UUID="06f9f665-777d-48b6-9a83-f4bf183a5f94" TYPE="ext4" 

```

This is the content of the /media/ea7728c0-d5fe-4914-a93a-5e089ca7ea1d/etc/fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
# /home was on /dev/sda8 during installation
# /var was on /dev/sda7 during installation
# swap was on /dev/sda6 during installation
UUID=47af9af9-cd50-4d79-882e-e6311a0fd780 none            swap    sw              0       0
/dev/disk/by-id/wwn-0x50024e9204f44665-part6 /mnt/wwn-0x50024e9204f44665-part6 auto nosuid,nodev,nofail,noauto,x-gvfs-show 0 0
/dev/disk/by-id/wwn-0x50024e9204f44665-part7 /mnt/wwn-0x50024e9204f44665-part7 auto nosuid,nodev,nofail,x-gvfs-show,noauto 0 0
/dev/disk/by-id/wwn-0x50024e9204f44665-part1 /mnt/wwn-0x50024e9204f44665-part1 auto nosuid,nodev,nofail,x-gvfs-show,noauto 0 0
```

---

### Post by erik1001 on 2013-01-04
Okay, I think I solved my problem. I've changed the contents of /etc/fstab to:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
# /home was on /dev/sda8 during installation
# /var was on /dev/sda7 during installation
# swap was on /dev/sda6 during installation
UUID=47af9af9-cd50-4d79-882e-e6311a0fd780 none            swap    sw              0       0
UUID=ea7728c0-d5fe-4914-a93a-5e089ca7ea1d / auto defaults 0 0
UUID=ab8cddf2-84c4-4f09-a94b-3e29e2b32e8d /var auto defaults 0 0
UUID=06f9f665-777d-48b6-9a83-f4bf183a5f94 /home auto defaults 0 0
```

Is it ok?

---

### Post by fdrake on 2013-01-04
make a copy of your fstab , then edit the fstab as follow (copy paste):
> 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
/dev/sda5 /home ext4  	defaults 0 0
# /home was on /dev/sda8 during installation
/dev/sda8 /home ext4  	defaults 0 0
# /var was on /dev/sda7 during installation
/dev/sda7 /var ext4  	defaults 0 0
# swap was on /dev/sda6 during installation
UUID=47af9af9-cd50-4d79-882e-e6311a0fd780 none            swap    sw              0       0
UUID=ea7728c0-d5fe-4914-a93a-5e089ca7ea1d / auto defaults 0 0
UUID=ab8cddf2-84c4-4f09-a94b-3e29e2b32e8d /var auto defaults 0 0
UUID=06f9f665-777d-48b6-9a83-f4bf183a5f94 /home auto defaults 0 0


save reboot into ubuntu

ps: did you change the fstab, previuosly?

---

### Post by erik1001 on 2013-01-04
fdrake, thanks. Should I change it again like you suggested or it is ok to use my configuration?
And actually I've changed the configuration using "Disks" application in Ubuntu. I've tried to disable automatical mounting of my USB HDD partitions, but I don't know why there were changes in my /etc/fstab file.

---

### Post by fdrake on 2013-01-04
> **erik1001 said:**
> fdrake, thanks. Should I change it again like you suggested or it is ok to use my configuration?
And actually I've changed the configuration using "Disks" application in Ubuntu. I've tried to disable automatical mounting of my USB HDD partitions, but I don't know why there were changes in my /etc/fstab file.

so it was the swap system that created the problem. glad you figured it out! :D

i didn't see your second post while posting. Well i Would add the lines about the /var /home and / system . you can comment them in front of it with a "#" . If in the future you have problems try to uncomment them-- but it is not neccessary! :D.

ps. wonder how the fstab gor changed like that ? any idea?

---

### Post by erik1001 on 2013-01-04
No idea. :( Thanks again. :)

---

