---
title: "MDADM raid volume (md0) disappeared when replacing drive"
date: 2017-08-18
forum: General Help
---

### Post by m3atwad on 2017-08-18
Hello,

I setup an ubuntu server and configured madm to create a raid 5 volume.  I have been trying to get an understanding of how to set it up as well as handle a drive failure and recover it from basic crashes.  

I have 3 drives (sdb, sdc, sdd) configured in raid 5 with my OS installed on a separate drive sda.  This worked fine and mounted fine at /mnt/md0 and the device showed up in /dev/md0.  Now I've disconnected one of the drives and plugged in a blank drive.  Upon doing this my /dev/md0 has disappeared and is no where to be found.  From reading about handling drive problems with mdadm everything i find uses the /dev/md0 (or whatever people set up the name to be) device to fix/repair/assemble etc....   This seems like a realistic scenario because a drive could crash and no longer function which is equivalent to me swapping a good one with a blank one.  Could someone give me some advice on what I should do or what direction I should go?

```
df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.4G     0  3.4G   0% /dev
tmpfs           692M  9.3M  682M   2% /run
/dev/sda1       104G  4.5G   94G   5% /
tmpfs           3.4G   19M  3.4G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.4G     0  3.4G   0% /sys/fs/cgroup
tmpfs           692M   48K  692M   1% /run/user/1000

lshw -C disk
  *-disk                  
       description: ATA Disk
       product: KINGSTON SA400S3
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 71E0
       serial: 50026B777600EC22
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=78c26229
  *-disk
       description: ATA Disk
       product: TOSHIBA HDWD130
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: ACF0
       serial: X6IEM46AS
       size: 2794GiB (3TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=b4fc6020-66b7-4ec6-86a7-e01e9248253b logicalsectorsize=512 sectorsize=4096
  *-disk
       description: ATA Disk
       product: TOSHIBA HDWD130
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdc
       version: ACF0
       serial: X6IEGLEAS
       size: 2794GiB (3TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=25a0e29f-a1ef-4919-b10c-bf8f54c7964e logicalsectorsize=512 sectorsize=4096
  *-disk
       description: ATA Disk
       product: Hitachi HUS72403
       vendor: Hitachi
       physical id: 0.1.0
       bus info: scsi@5:0.1.0
       logical name: /dev/sdd
       version: A5F0
       serial: P8GRBT5R
       size: 2794GiB (3TB)
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096

cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
unused devices: <none>

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=4e7d0aef-310d-479c-a743-bee2d24c566c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=aa69203e-4123-4f26-93b6-30a3bc8047df none            swap    sw              0       0

cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Mon, 14 Aug 2017 20:45:07 -0700
# by mkconf $Id$
ARRAY /dev/md0 metadata=1.2 name=REI-Remote:0 UUID=b932b176:d5f1ab01:57438d56:8feb12c1
```

---

### Post by wildmanne39 on 2017-08-18
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by m3atwad on 2017-08-19
Oops sorry about that!  Will do.

---

### Post by m3atwad on 2017-09-03
Does anyone have any info regarding this?  I"m still working on this and having issues.  I've setup a raid 0 array with 3 disks and a hot spare 4'th disk.  When I power down and unplug one of the "raided" disks and boot back up the array goes inactive and doesn't automatically rebuild itself.  Whey doesn't mdadm seem to figure out the disk is missing and automatically incorporate the hot spare?

---

### Post by gordintoronto on 2017-09-03
RAID 0 has no redundancy. If a drive fails, the array fails.

[http://searchstorage.techtarget.com/definition/RAID-0-disk-striping](http://searchstorage.techtarget.com/definition/RAID-0-disk-striping)

---

### Post by m3atwad on 2017-09-07
Well I understand there is no redundancy and the array will fail, but my understanding was that was repairable.  If one drive fails I thought you could add a new drive and rebuild the array with mdadm.  Are you making the point that this is not possible?

---

### Post by mastablasta on 2017-09-07
> **m3atwad said:**
> Well I understand there is no redundancy and the array will fail, but my understanding was that was repairable.  If one drive fails I thought you could add a new drive and rebuild the array with mdadm.  Are you making the point that this is not possible?

yes, that is not possible with RAID 0.

as for the rebuild have a look here: [https://superuser.com/questions/603481/how-do-i-reactivate-my-mdadm-raid5-array](https://superuser.com/questions/603481/how-do-i-reactivate-my-mdadm-raid5-array)

also 

```
man mdadm
```

---

