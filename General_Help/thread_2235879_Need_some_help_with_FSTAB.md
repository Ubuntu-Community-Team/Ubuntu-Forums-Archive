---
title: "Need some help with FSTAB"
date: 2014-07-23
forum: General Help
---

### Post by Gieter on 2014-07-23
Hello all,

After some years im stepping back into linux. So excuse me if im a bit rusty.

I was working on a small server with a RAID 1 setup. The RAID has been setup properly, but everytime i tried to mount it, it came in media, which didnt work out as i need to use the space for FTP.

Anyway a long story short, im wrestling with fstab at this moment, been reading up on it last 30 minutes, tried to find something with a proper GUI, alass, not getting any closer.

If someone can give me some pointers on how to do this in a quick and effective way, would be greatly appreciated. 

EDIT: Extra info
```
fdisk -l 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0005a8b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1953523711   976760832   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00072c96

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953523711   976760832   fd  Linux raid autodetect

Disk /dev/sdc: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002001b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048      499711      248832   83  Linux
/dev/sdc2          501758   250068991   124783617    5  Extended
/dev/sdc5          501760   250068991   124783616   8e  Linux LVM

Disk /dev/md0: 1000.1 GB, 1000068677632 bytes
2 heads, 4 sectors/track, 244157392 cylinders, total 1953259136 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/mapper/Binnenhuis--vg-root: 119.5 GB, 119546052608 bytes
255 heads, 63 sectors/track, 14533 cylinders, total 233488384 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/Binnenhuis--vg-root doesn't contain a valid partition table

Disk /dev/mapper/Binnenhuis--vg-swap_1: 8229 MB, 8229224448 bytes
255 heads, 63 sectors/track, 1000 cylinders, total 16072704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


```

Fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/Binnenhuis--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdc1 during installation
UUID=0c6efcf8-38f7-44b2-9cca-226bda11a5db /boot           ext2    defaults        0       2
/dev/mapper/Binnenhuis--vg-swap_1 none            swap    sw              0       0

```




Regards

---

### Post by steeldriver on 2014-07-23
Can you be a bit more specific? what exactly are you having trouble with? Basically you need to:

1. find the block device pathname (for a RAID volume this would probably be a symbolic name provided by the device mapper) or UUID 

```

sudo blkid -c /dev/null

```

2. choose and/or create an empty directory somewhere in the filesystem to act as a mount point for the volume

3. add a line to the /etc/fstab file with the 2 above fields plus the filesystem type and appropriate mount options

---

### Post by Gieter on 2014-07-23
Hi Steeldriver,

1:
```
kevin@Binnenhuis:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="b5c39d74-0179-a43b-4903-98bff732cca7" UUID_SUB="f490b40e-6b71-f8a6-bedd-b04aae924a33" LABEL="Binnenhuis:0" TYPE="linux_raid_member" 
/dev/sdb1: UUID="b5c39d74-0179-a43b-4903-98bff732cca7" UUID_SUB="f4fa3fbe-0de2-4566-fb35-c4af39274d21" LABEL="Binnenhuis:0" TYPE="linux_raid_member" 
/dev/sdc1: UUID="0c6efcf8-38f7-44b2-9cca-226bda11a5db" TYPE="ext2" 
/dev/sdc5: UUID="zDYK56-qi1G-ZOH2-N8Yk-RZB1-qwkZ-3YBU78" TYPE="LVM2_member" 
/dev/md0: UUID="47f65a56-5c84-40bd-9234-c623d8ada976" TYPE="ext4" 
/dev/mapper/Binnenhuis--vg-root: UUID="563cbee1-693b-4b12-8d04-4b77d6119a18" TYPE="ext4" 
/dev/mapper/Binnenhuis--vg-swap_1: UUID="1ec39c7c-dd37-4e35-8cad-976e32c4b4bf" TYPE="swap" 

```

2:
I feel like a total idiot, but if i recall correctly it had to be mounted in a specific location back in the day. 

At this moment it does not mind where it is mounted, As long it is auto mounted and accessible without a user logged in. (PROFTPD)

3.
I will try to do such a thing, it doesnt sound too hard, but always a bit finicky to **** things up in fstab files.

---

### Post by Gieter on 2014-07-23
If possible, can someone give me an example for what i need to add to fstab? so i can edit it and paste it in (yeah i know im lazy) But would make my life a lot easier at the moment.

---

### Post by steeldriver on 2014-07-23
AFAIK there are no strict rules about mount points - more like guidelines. Old school was to put anything that was local but non-standard under /mnt e.g. /mnt/ftp, the newer convention is to consider the purpose of the files e.g. if they are related to some service that the box is providing, put them under /srv. If it's not related to anything in particular you could use a generic pathname like /data or /storage, or /mnt/storage, or whatever. It's really up to you and what's convenient for your users.

You'll probably want to test it first by manually mounting e.g.

```

sudo mkdir -p /storage/whatever

sudo mount -t ext4 /dev/md0 /storage/whatever

```

If that works, you can move on to adding it to your fstab file

---

### Post by Gieter on 2014-07-23
Grand, testing this as we speak.

---

### Post by Gieter on 2014-07-23
tested this, works as a charm.

FTP is avaible at all times now. 

Then the point remains: How do i bind this to fstab.
 

Really apreciate the help!

---

### Post by steeldriver on 2014-07-23
OK if that works and gives you the required access then you don't need to worry about setting any non-default mount options, you can just add a line like

```

/dev/md0      /storage/whatever      ext4      defaults    0    2

```
or
```

UUID=47f65a56-5c84-40bd-9234-c623d8ada976      /storage/whatever      ext4      defaults    0    2

```

TBH I don't know the pros and cons of using UUID versus /dev/md0 - in the case of regular block devices (/dev/sda1 etc.) there's a clearer case for using UUIDs since the numbering can change between boots, however if your RAID is properly configured via /etc/mdadm.conf (and written into initramfs) then the /dev/md0 mapping should not change (and also it make it clearer that it's a RAID array).

Also I'm hazy on the last 2 parameters but I think that "0" and "2" should be OK.

You can then manually unmount the device and see if it correctly remounts via the new fstab entry

```

sudo umount /dev/md0

sudo mount -a

```

---

### Post by Gieter on 2014-07-23
At this moment i was editting it with nano, I dont know how big a problem or how precise the spacing is in these files, should i consider using another program to edit these files/tables?

---

### Post by steeldriver on 2014-07-23
Using nano is fine - there needs to be some whitespace between the fields and each entry must be on a single line, but beyond that it's just esthetics - you can space it out to make it look nicer

---

