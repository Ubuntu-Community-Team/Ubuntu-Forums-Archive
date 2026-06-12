---
title: "Cant Access to NTFS"
date: 2008-05-04
forum: General Help
---

### Post by talisfang on 2008-05-04
I installed Ubuntu by wubi and my ntfs drives were not mounted automatically. I was trying to make it. I right clicked and went to properties. Before the Volume tab there was a tab about hard disk and mount points. In it there was mount points and two more sections. I filled them with whats written in the volume tab. But i cant reach my ntfs drives now. 

Error is:
 Cant Mount
Details: mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

When i right click my ntfs drive i cant see the tab i changed. Please Help...

---

### Post by DaddyX3 on 2008-05-04
Enter in terminal: 
```
sudo blkid
```
and paste back here. Then run: 
```
gedit /etc/fstab
```
and paste back here so we know what we are dealing with.

---

### Post by talisfang on 2008-05-05
sudo blkid:
/dev/sda1: UUID="9AE85057E850342B" TYPE="ntfs" 
/dev/sda5: UUID="60E43FCDE43FA466" LABEL="Yerel D" TYPE="ntfs" 
/dev/sda6: UUID="01C89757E2053480" LABEL="E" TYPE="ntfs" 
/dev/sda7: UUID="01C8975627C0FD80" LABEL="DEPO" TYPE="ntfs" 
/dev/loop0: UUID="d1cf1992-07f3-4f7c-ae69-a6b3be6a0f8c" TYPE="ext3" 

gedit /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Siyfion on 2008-05-05
Im having a similar problem, although the NTFS drive I am trying to access is on a RAID 1 array.. Although I don't think thats the problem. (As my main drive is on a RAID 0, all the RAID stuff is installed)

---

### Post by talisfang on 2008-05-05
I solved my problem by NTFS Configuration Tool. I installed it by Add/Remove. After the installation you can find it under system tools

---

### Post by Siyfion on 2008-05-05
I tried that but it continues to fail to mount the volume.. :(

---

### Post by DaddyX3 on 2008-05-05
You will need to make sure that your raid is --assembled before you will have your raid drives bootable. if you use mdadm then the command would be something like: 
```
sudo mdadm --assemble --scan
```
I'm not sure about dmraid (I don't use it). Then you would want to ```
Sudo mount -a
```
You should have your raid assembled and listed as one drive. At this point you need to enter that  new raid array mount by editing your fstab file. I would do a 
```
sudo fdisk -l
```
and a 
```
gedit /etc/fstab
```
and paste back your results if you need some more help.

---

### Post by Siyfion on 2008-05-05
My array is already up and running, and functioning perfectly, like I said, the main drive with the "/" filestructure on it, I am writing this from now!

I have two "drives" /dev/mapper/ddf1_Master & /dev/mapper/ddf1_Slave

It's the Slave which I can't get to mount properly.. Even though when I was using the LiveCD it mounted it just fine!?

I get a "Cannot mount volume. Unable to mount volume 'SafeDrive'."

---

### Post by DaddyX3 on 2008-05-05
Like I said post your drive info from fdisk -l and from your fstab, then get some UUID info from: sudo blkid and maybe we can get that fixed. I can't help you unless you post your info.

---

### Post by Siyfion on 2008-05-05
fdisk -l
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9cbfc826

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         487     3911796   82  Linux swap / Solaris
/dev/sda2   *         488       77776   620823892+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x87b9c31a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30500   244982784    7  HPFS/NTFS

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x87b9c31a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30500   244982784    7  HPFS/NTFS

Disk /dev/dm-0: 250.8 GB, 250865516544 bytes
255 heads, 63 sectors/track, 30499 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x87b9c31a

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *           1       30500   244982784    7  HPFS/NTFS

Disk /dev/dm-1: 639.7 GB, 639729926144 bytes
255 heads, 63 sectors/track, 77776 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9cbfc826

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1               1         487     3911796   82  Linux swap / Solaris
/dev/dm-1p2   *         488       77776   620823892+  83  Linux

Disk /dev/dm-2: 250.8 GB, 250862370816 bytes
255 heads, 63 sectors/track, 30498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-2p1   ?         410      119791   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
/dev/dm-2p2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-2p3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/dm-2p4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-3: 4005 MB, 4005679104 bytes
255 heads, 63 sectors/track, 486 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-3 doesn't contain a valid partition table

Disk /dev/dm-4: 635.7 GB, 635723665920 bytes
255 heads, 63 sectors/track, 77289 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-4 doesn't contain a valid partition table

```

fstab
```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=81096f45-f081-44c1-bfe4-5863e7d5e281 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=dcf32922-5dfb-47c8-834b-cd8353da509e none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdd1 /media/SafeDrive ntfs-3g defaults,locale=en_GB.UTF-8 0 0
```

blkid
```
/dev/mapper/ddf1_Master2: UUID="81096f45-f081-44c1-bfe4-5863e7d5e281" TYPE="ext3" 
/dev/mapper/ddf1_Master1: TYPE="swap" UUID="dcf32922-5dfb-47c8-834b-cd8353da509e" 
/dev/mapper/ddf1_Slave1: UUID="866E7F246E7F0C65" LABEL="SafeDrive" TYPE="ntfs" 
/dev/sdc1: UUID="866E7F246E7F0C65" LABEL="SafeDrive" TYPE="ntfs" 
/dev/sdd1: UUID="866E7F246E7F0C65" LABEL="SafeDrive" TYPE="ntfs" 
/dev/mapper/ddf1_Slave: UUID="1ed12941-a3fc-4cdc-8477-14d601a28cdc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda1: TYPE="swap" UUID="dcf32922-5dfb-47c8-834b-cd8353da509e" 
/dev/dm-0: UUID="1ed12941-a3fc-4cdc-8477-14d601a28cdc" SEC_TYPE="ext2" TYPE="ext3" 

```

When I open up "My Computer" I see TWO "SafeDrive"'s and one SCSI drive.. none of which I can open!

---

### Post by DaddyX3 on 2008-05-05
Well, I might need a little help from you on this one to try and decipher what you have exactly. I see that you have dmraid installed? How many raid arrays do you have? Is the raid array ntfs? I'm looking at your UUID#'s and both drives that you can not mount or get access to, has the identical UUID#!!! This would only make sence if it was possible a raid array and is being seen as one but then it doesn't make since that it is getting seen twice by the blkid. Can you help me out on what you have got going on here? I'm also not proficient in dmraid, but I think I can make heads or tales of it enough to get things mounted right in fstab.

---

### Post by Siyfion on 2008-05-05
Ok, I have four drives...

Firstly, two 250GB's raided together in a RAID 1 (so still 250GB in size) called "Slave" but labelled as "SafeDrive".

Secondly, two 320GB's raided together in a RAID 0. (so 640~GB in total), called "Master".

---

### Post by DaddyX3 on 2008-05-05
OK, I'm going try and get this story straight. Sorry for the confusion, but its rather hard to gather context of what your saying with writing. Anyway, You are having troubles mounting your Raid 1 (mirroring) array. I would then take this to be /dev/dm-0 or /dev/dm-2 from your output on your fdisk -l post. Since they are a mirror image of eachother you will have a 50/50 chance at mounting the right one. So if you want to mount that to lets say /media/SafeDrive then you will need to edit the last line on your fstab file to: 
/dev/dm-0     /media/SafeDrive      defaults     ntfs      0    2    
This will mount the dm-0 raid to /media/SafeDrive. If this doesn't work, just try the other dm-2 and see if that works. 

ps- make a backup of your fstab before you edit it, in case you have troubles: 
```
sudo cp /etc/fstab /etc/fstab_backup
```
If you run into problems and cant boot back in for some reason enter grub and select safe mode and when it drops you to command line: 
```
sudo cp /etc/fstab_backup /etc/fstab
```
then restart.

---

### Post by Siyfion on 2008-05-06
Ok I kinda understand what your trying to do, so I had a go myself at editing it, to the following:

```
proc /proc proc defaults 0 0
/dev/mapper/ddf1_Master2 / ext3 relatime,errors=remount-ro 0 1
/dev/mapper/ddf1_Master1 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/mapper/ddf1_Slave /media/SafeDrive ntfs-3g defaults,locale=en_GB.UTF-8 0 0

```

As I realize now, every boot up it is having to search for my main drive by UUID, and the swap partition just fails. However if I do a "sudo swapon /dev/mapper/ddf1_Master1" it works..


After editing this, it changed NOTHING though.. The drive's still search by UUID, SafeDrive still appear's twice and the swap fails to mount.. I don't get it, as the old file HAS UUID's in it, but I removed them from this one!?

It's almost like dmraid hasn't started up before it tries to access the drives..?

---

### Post by Siyfion on 2008-05-06
Ok... I changed the /dev/mapper/ddf1_Slave to /dev/mapper/ddf1_Slave1 and it now mounts the drive correctly! Yay! Although I still have 3 icons for the "SafeDrive" in my computer, only one works thou! :S

And my main drive and swap drive still aren't quite right.. On startup it keeps sayiong something about resuming from previous blah.. and gets the driives by UUID..?

---

### Post by DaddyX3 on 2008-05-07
Believe me, I'm just as confused as you are with your fstab and drive configuration! I'm not familure with dmraid (I've never used it) And as far as your mirrored Raid array, I don't know which one you should be accessing and writing to. Your fstab and fdisk output are pretty messed up looking to me. I hope you can get things squared away.

---

### Post by Siyfion on 2008-05-07
Well it works now.. So I ain't complaining! lol.

---

