---
title: "Error mounting filesystem on Ubuntu 14.04"
date: 2015-04-05
forum: General Help
---

### Post by au.9108321 on 2015-04-05
Hello ladies and gentlemen

Some days ago my pc "fell down" , about 3 inches, it was turned on at the moment and after the impact the screen froze but it didn't turn off, i simply restarted it and ran ok but during the mounting /dev/sda/____ (i dont remember which partition was the one showed here) it showed that it was having trouble loading the partition to load but it did, afterwards i updated it when prompted to by the** Software Update**, i also updated from terminal, the disk is a hdd, somewhat old and it already had some damaged sectors but not enough to consider buying a new disk.

While updating and using it Software Update froze, screen went dark and i cut the power

Finally i turned it on, updated it, used it, and while surfing the web with around 60 tabs open using Chromium, i left it doing nothing with the browser still open(16gb of ram, processor AMD FX8120) came back many hours later and started watching a video i left preloading (sh*tty ISP with low bandwidth), suddenly it deactivated the fullscreen mode, i thought flash had only crashed but then the screen blinked then the launcher disappeared as well as the upper title bar, the browser was still there not frozen i could move between tabs, i tried to Ctrl + Alt + T to open a terminal and see what was going on but it didnt open then the browser closed after a few minutes and i was left with only the cursor on the screen(it wasn't frozen) but since i couldn't invoke the launcher or anything via keyboard shortcut i cut the power and restarted

And then sh*t just hit the fan, it send me directly after taking a while and showing the purple screen while loading the system then send me something like this 

BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a lost of built-in commands.
(initramfs)it didn't say why it send me here, but it did it everytime i retried


Didn't panic and restarted while pressing ESC during the purple screen to see the processes running and several of them said error, then restarted again and tried with the older different kernels, and NOPE, then did a memory test and it didn't show any errors, so right now i'm with the liveUSB but i'm stuck, gparted said this
[SIZE=1]
Partition            File System              Size                    Used                 Unused                Flags
/dev/sda1          ext4                        915.53 GiB          170.61 GiB        744.92 GiB           boot                             
[/SIZE]/dev/sda2          extended                 15.98 GiB                   —                    —                        
   /dev/sda5&#10071;&#65039;    unknown                  15.98 GiB[SIZE=1]                  —                     [/SIZE]—

I tried taking screenshots while using the liveUSB and cannot make it work, dunno why
Ubuntu's disk utility said this

______________________________________________
[SIZE=1]1.0 TB Hard Disk
/dev/sda/

Model ST31000528AS (CC38)
Size 1.0 TB (1,000,204,886,016 bytes)
Partitioning Master Boot Record
Assessment Disk is OK, 2267 bad sectors (34º C / 93º F)
______________________________________________

Volumes:

Filesystem Partition 1     983 GB Ext4      Device /dev/sda1     Partition Type Linux (Bootable)      Contents Ext4 (version 1.0) - Not Mounted
[/SIZE]Extended Partition 2       17 GB               Device /dev/sda2     Partition Type Extended                Contents Extended Partition
Partition 5                     17 GB               Device /dev/sda5     Partition Type Linux swap              Contents Unknown

(i tried to mount the disk from here since it didnt do it automatically) and it said this:

[SIZE=1]**Error mounting filesystem**[/SIZE] 
[SIZE=1]Error mounting /dev/sda1 at /media/it/1bf6ff55-242c-4a9d-8d91-04414ba93458: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda1" "/media/it/[/SIZE]1bf6ff55-242c-4a9d-8d91-04414ba93458" exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock, on /dev/sda1,
[SIZE=1]   missing codepage or helper program, or other error
   In some cases useful info is found in syslog - try
   dmesg | tail or so

(udisk-error-quark, 0)
 [/SIZE]
So... please help, i dunno if i simply should (re-)install grub to see if i can link the partitions again, or how to fix that partition, should i try something else?? 

I used to see if i could find where the problem was and i got this (i've tried taking a screenshot while using the liveCD and cannot make it work

[FONT=Ubuntu Mono][COLOR=#000000]sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Device         Boot          Start          End          Blocks          Id    System
/dev/sda1        *            2048    1920008191      960003072          83    Linux
[/COLOR][/FONT]/dev/sda2                  1920010238    1953523711         16756737            5    Extended
/dev/sda5                  1920010240    1953523711         16756737           82    Linux swap / Solaris


[FONT=Ubuntu Mono][COLOR=#000000]Disk /dev/sdf: 15.5 GB, 15512174592 bytes
32 heads, 63 sectors/track, 15028 cylinders, total 30297216 sectors


Device     Boot      Start          End      Blocks      Id      System
/dev/sdf1   *           63     30296447   15148192+       c      W95 FAT32 (LBA)




sudo parted -l
Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector Size (logical/physical): 512B / 512B
Partition Table msdos

Number    Start    End      Size    Type     File system      Flags
1         1049kB   983GB    983GB   primary  ext4             boot                                  
2         983GB    1000GB   17.2GB  extended                                          
5         983GB    1000GB   17.2GB  logical                                          




sudo blkid
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="1bf6ff55-242c-4a9d-8d91-04414ba93458"  TYPE="ext4"
/dev/sdf1: LABEL="MULTIBOOT" UUID="080C-3F31" Type="vfat"[/COLOR][/FONT]

---

### Post by bab1 on 2015-04-05
[QUOTE]Error mounting /dev/sda1 at /media/it/1bf6ff55-242c-4a9d-8d91-04414ba93458: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda1" "/media/it/1bf6ff55-242c-4a9d-8d91-04414ba93458" exited with non-zero [B][I]exit status 32: mount: wrong fs type, bad option, bad superblock, on /dev/sda1,
missing codepage or helper program, or other error[/I][/B]
In some cases useful info is found in syslog - try
dmesg | tail or so

(udisk-error-quark,
My guess is the HDD is damaged (crashed).  The impact most likely caused the HDD heads to hit the moving platters.  You could try *fsck* to see if you can restore the file system on that partition with this command ```
sudo fsck /dev/sda1
```

---

