---
title: "Software Raid Assistance Requested"
date: 2008-06-28
forum: General Help
---

### Post by S33KER on 2008-06-28
I built a new system recently and wanted to add software RAID1 capability.  I had a 500Gig IDE drive I used to install 8.04 on and it appears that Ubuntu defaulted to SDC for this drive.  Based on what I found on the internet the developers found that the SCSI drivers worked as good or better for the IDE drives which is why IDE drives now show up as /dev/sdX rather than the old /dev/hdX drives.  I purchased two SATA2 750Gig drives and wandered the internet looking for instructions on how to set up a software RAID.  I found instructions on how to do this with mdadm and managed to get the raid up and running with the detailed instructions on partitioning, configuring the file type, creating the raid, activating it, etc.  The problem I need help with is that since then I've found out that the newer distros of Linux (Ubuntu included) don't always assign the drives the same way each time on bootup.  The original setup had the 500G as sdc and the two 750G drives as sda and sdb.  The mdadm.conf file indicated that it had built a level 1 raid using 2 devices /dev/sda1 and /dev/sdb1.  The next time I booted the system the 500G drive became sda and the two 750G drives were sdb and sdc.  The fstab entry for the /dev/md0 raid reported a superblock error naturally since it was trying to pair the 500G sda with the 750G sdb drive that was initially setup.  I have spent numerous hours trying everything I can find on the internet and every suggestion that all my linux guru buddies have suggested to "lock" the drive assignment order and nothing has worked.  Even they can't seem to figure out how to stabilize the drive orders.  The system needs to keep the 500G as sda and the 2 750G drives as sdb and sdc.

Examples of what I've tried:
Since system assigned the IDE drive as sdc originally it was thought that if I put the two SATA drives on SATA4 and SATA5 they would come up "behind" the sdc drive as sde and sdf.  Not so.  

I found suggestions that the BIOS may have an effect.  The bios is set to boot off the 500G drive and boot it does but the drive may be sda one time and sdc the next.  

I've tried using fstab to control the order of the drives but this doesn't seem to work as the two 750G drives have a UUID that is applied to both of them as /dev/md0.  

I've researched using GRUB to control boot sequence but nothing I've read indicates that this will work as the GRUB setup seems to point to HD0,0 as the location of the boot drive and since it boots I'm not sure when the sdX assignments gets done.  

I can normally muddle my way through things like this or bug the guys I work with who live and breath linux but in this instance even they are stumped.

Anybody bumped into this and have a solution?  I'd really appreciate the help.

Thanks in advance for any assistance.


Never mind. . . 

Got tired of fighting it so I went and bought an eSATA RAID enclosure.  It looks like a single drive to the system and my RAID is online now.

---

### Post by fjgaude on 2008-06-28
What you have run across is normal and causes no issues the way Ubuntu uses UUIDs in the /etc/fstab file and the way md, mdadm uses its own way of knowing what drives are part of an array, through the use of the superblock and UUID. The latter is the same for all array drives, so /dev/sd[nn] can change all around without affect either the boot up or the array assembly.

All works with Ubuntu and mdadm software raid. Let the name of the drives go as they will.

---

### Post by S33KER on 2008-06-28
fjgaude - Thanks for the reply.  That is not what happens on my system.  I can boot the computer multiple times and its behavior changes with each boot.  If the system boots with the 500G as sdc and the other 2 as sda and sdb then bootup will finish, everything works fine and I can access the RAID.  If the system assigns the 500G as anything other than sdc then Ubuntu hangs with a superblock error on /dev/md0, drops to a terminal and instructs me to do a manual repair on the file system.  I can go ahead and let the system finish booting but /dev/md0 does not exist and naturally neither does my RAID mount point.

---

### Post by fjgaude on 2008-06-28
Show us your /etc/fstab file... it should be using UUIDs for the swap and boot drives.

---

### Post by S33KER on 2008-06-29
It does. . . 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cea6e66e-2d53-4cdc-b541-28586792ff2b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f94163ca-78f2-4722-959c-2ca2d6663643 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
# eSTATA 750G Raid
UUID=f8329712-eaf3-4314-9c5c-3fd4cc41a581      /mnt/750G_Raid     ext3          defaults               0     2

The /dev/sda1 line has always looked as it does above.  Ever since I built the system.  That's why I was surprised when an fdisk -l would show the 500G as sdc.  Since I installed the eSATA RAID and it only sees 2 drives the 500G has been sda every time I boot.  Since it is working now and the RAID mounts I'm going to leave well enough alone.

I appreciate your attempt to help and I thank you for responding.

---

### Post by fjgaude on 2008-06-29
The UUID in the fstab file, you obtained that from something like **blkid**, or from other programs?

I'm interested to learn workarounds in helping folks solve issues like this. Once an array is created using its name, e.g., /dev/md0, in the fstab has always worked for me, because mdadm doesn't use drive names to auto assemble at boot-up. In other places drive UUIDs works no matter what the names change to. Ubuntu and Linux is almost there with these issues... soon.

Thanks for all the info you have provided.

---

### Post by S33KER on 2008-06-29
The UUID for the 500G (sda) was there from the install I believe.  I don't remember setting it up as I didn't have much experience with such when I first built the system.  Due to all the research I did trying to bring the mdadm RAID online I learned how to use blkid to locate the UUID so when I configured the eSATA drive I intentionally used the UUID rather than the /dev/sdX to explicitly set the mount point of the /mnt/750G_Raid.

BTW, I thought mdadm did use names since the mdadm.conf listed /dev/sda and /dev/sdb as the 2 devices that made up /dev/md0?  I noticed when mdadm created the UUID and inserted it into the fstab there was only a single UUID for the RAID partition but I couldn't locate the UUID of the individual drives/partitions as I had thought I could use the UUIDs in the mdadm.conf file to explicitly define which partitions to use for the RAID.

---

### Post by S33KER on 2008-06-29
Here's the kind of thing I'm talking about.  On my previous 7 bootups of the computer the 500G was /dev/sda.  This boot now shows the below when I did a sudo fdisk -l:

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0921ddd5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       91201   732572001   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002b581

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       59579   478568286   83  Linux
/dev/sdb2           59580       60801     9815715    5  Extended
/dev/sdb5           59580       60801     9815683+  82  Linux swap / Solaris


I just picked up 2 more 750Gig drives to continue experimenting with since I have the backup I need on the eSATA.  I really do want to understand what is going on so I'll continue tinkering.

---

### Post by S33KER on 2008-06-29
Just added the 2 new 750G drives.  Here's what fdisk now has to say:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002b581

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59579   478568286   83  Linux
/dev/sda2           59580       60801     9815715    5  Extended
/dev/sda5           59580       60801     9815683+  82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0921ddd5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   83  Linux

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Notice sda and sdb have swapped position in relation to drive names from the previous boot.  I'm going to fdisk the 2 new drives as type fd - Linux raid auto.

---

### Post by S33KER on 2008-06-29
Did an fdisk to create Linx raid auto partitions on /dev/sdb and /dev/sdc.  

Created a raid using:
sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
mdadm: size set to 732571904K
mdadm: array /dev/md0 started.

Did a:
mdadm --detail --scan > /dev/mdadm/mdadm.conf
to create the config file.

Used data from
more /etc/mdadm/mdadm.conf
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=2a80949a:12b025eb:9a0b587b:6e403cdc

to set fstab to 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cea6e66e-2d53-4cdc-b541-28586792ff2b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f94163ca-78f2-4722-959c-2ca2d6663643 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
# eSTATA 750G Raid
UUID=f8329712-eaf3-4314-9c5c-3fd4cc41a581      /mnt/750G_Raid     ext3          defaults               0     2
# 750G Software Raid
UUID=2a80949a:12b025eb:9a0b587b:6e403cdc       /mnt/750G_RaidB	  ext3	        defaults               0     2

Now to wait for resync to finish so I can test the RAID.

---

### Post by S33KER on 2008-06-29
OK, the resync finished and I put a file system on the RAID with **mkfs -j /dev/md0**.  It appeared to work correctly so I rebooted.

On reboot I get:
/dev/sda1: clean, 193514/45793280 files, 63532096/183143000 blocks
fsck.ext3: Unable to resolve 'UUID=2a80949a:12b025eb:9a0b587b:6e403cdc'
fsck died with exit status 8

The system drops into a terminal as root for troubleshooting.  I can Ctrl-D to continue the boot process and the system comes up OK.  I found that the mdadm was not bringing up the RAID array.  I had to do a **modprobe md** before a **mdadm -A /dev/md0** would start the RAID.  A web search indicated that a **dpkg-reconfigure mdadm** needed to be done to make mdadm start properly.  I did that and it was only partially useful.  On boot I still get the "Unable to resolve. . ." error.  I can bypass the error and find that once booted the RAID has now been started and I can do a mount against it but I cannot seem to get past the fsck error.  It appears as if the RAID array hasn't been started by the time the fsck against the fstab is invoked.

---

### Post by fjgaude on 2008-06-30
Notice the UUIDs in your fstab file are not all alike in terms of format: one uses "-" and the other uses ":" as separaters. The one with the ":" is the way **mdadm**, **md** assigns a UUID to an array and all the drives of the array. This single UUID is what mdadm uses to assemble an array, which I think is in the superblocks of each drive.

Such is not the UUID you get with blkid, and used to mount drives and what should be used in an fstab line to mount an array. I always simply use the /dev/md[nn] and it has always worked.

I admit, there's lots to learn and it only takes doing one little thing incorrectly to set things off to being strange or bad.

I have wished for the developers of md and mdadm to write a book on the subject, with all the things one has to do to run and maintain a vast set of arrays. But I can't see one coming as the market is just so small for such a book. Until then we have **man mdadm**, which seems to get updated with just about every kernel update. Small changes, additions expanding the depth of the man pages.

Hang in there, man... we all learn together.

---

### Post by S33KER on 2008-06-30
My Linux buddies caught that right away when I described what was happening.  I had the UUID of the RAID array not the file system that was ON the array.  That was the last piece of the puzzle.  I now have a fully functional software RAID 1 based on the direction you gave me.

Thanks for the information, it was just enough to get me to go back and try one more time.

---

### Post by fjgaude on 2008-07-01
Great, success is always at hand, if we don't give up and faint. <smile>

---

