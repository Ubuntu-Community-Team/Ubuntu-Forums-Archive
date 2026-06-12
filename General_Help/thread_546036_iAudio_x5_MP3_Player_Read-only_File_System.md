---
title: "iAudio x5 MP3 Player Read-only File System"
date: 2007-09-08
forum: General Help
---

### Post by optimus.prime on 2007-09-08
Well folks, after inadvertantly tripping over the cord to my MP3 player while it was writing a large chunk of data, I seem to have come across a problem that not many have experienced before (from a general Google search).

Upon remounting it and attempting to access it, I am given the unceremonious (and unhelpful!) message that the device is a read-only file system. Well, my first instinct was to try and issue a general 

chmod -R 777 /media/IAUDIO and/or chmod -R 777 /dev/sdb1 command

Both just spat out some errors about it being read only.

Then I attempted to access the disk from nautilus as root, to see if I could change the permissions in that way. No dice.

dmesg produces this:

_______________________________________________________________
[ 1378.892000] scsi 9:0:0:0: Direct-Access     TOSHIBA  MK3006GAL        BY10 PQ: 0 ANSI: 0 CCS
[ 1378.892000] SCSI device sdc: 58605120 512-byte hdwr sectors (30006 MB)
[ 1378.896000] sdc: Write Protect is off
[ 1378.896000] sdc: Mode Sense: 00 4a 00 00
[ 1378.896000] sdc: assuming drive cache: write through
[ 1378.900000] SCSI device sdc: 58605120 512-byte hdwr sectors (30006 MB)
[ 1378.904000] sdc: Write Protect is off
[ 1378.904000] sdc: Mode Sense: 00 4a 00 00
[ 1378.904000] sdc: assuming drive cache: write through
[ 1378.904000]  sdc: sdc1
[ 1379.256000] sd 9:0:0:0: Attached scsi disk sdc
[ 1379.256000] sd 9:0:0:0: Attached scsi generic sg1 type 0
[ 1383.536000] FAT: Filesystem panic (dev sdc1)
[ 1383.536000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1383.536000]     File system has been set read-only
[ 1383.536000] FAT: Filesystem panic (dev sdc1)
[ 1383.536000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1383.544000] FAT: Filesystem panic (dev sdc1)
[ 1383.544000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1383.544000] FAT: Filesystem panic (dev sdc1)
[ 1383.544000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1383.544000] FAT: Filesystem panic (dev sdc1)
[ 1383.544000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1383.548000] FAT: Filesystem panic (dev sdc1)
[ 1383.548000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1383.548000] FAT: Filesystem panic (dev sdc1)
[ 1383.548000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1383.548000] FAT: Filesystem panic (dev sdc1)
[ 1383.548000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1383.548000] FAT: Filesystem panic (dev sdc1)
[ 1383.548000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1383.548000] FAT: Filesystem panic (dev sdc1)
[ 1383.548000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1383.960000] FAT: Filesystem panic (dev sdc1)
[ 1383.960000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1383.960000] FAT: Filesystem panic (dev sdc1)
[ 1383.960000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1383.960000] FAT: Filesystem panic (dev sdc1)
[ 1383.960000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1383.964000] FAT: Filesystem panic (dev sdc1)
[ 1383.964000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1383.964000] FAT: Filesystem panic (dev sdc1)
[ 1383.964000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1396.944000] FAT: Filesystem panic (dev sdc1)
[ 1396.944000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1396.944000] FAT: Filesystem panic (dev sdc1)
[ 1396.944000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1396.944000] FAT: Filesystem panic (dev sdc1)
[ 1396.944000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1396.944000] FAT: Filesystem panic (dev sdc1)
[ 1396.944000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1396.944000] FAT: Filesystem panic (dev sdc1)
[ 1396.944000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1405.848000] FAT: Filesystem panic (dev sdc1)
[ 1405.848000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1405.848000] FAT: Filesystem panic (dev sdc1)
[ 1405.848000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1405.848000] FAT: Filesystem panic (dev sdc1)
[ 1405.848000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1405.848000] FAT: Filesystem panic (dev sdc1)
[ 1405.848000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1405.848000] FAT: Filesystem panic (dev sdc1)
[ 1405.848000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1414.884000] FAT: Filesystem panic (dev sdc1)
[ 1414.884000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1414.884000] FAT: Filesystem panic (dev sdc1)
[ 1414.884000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1414.884000] FAT: Filesystem panic (dev sdc1)
[ 1414.884000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1414.884000] FAT: Filesystem panic (dev sdc1)
[ 1414.884000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1414.888000] FAT: Filesystem panic (dev sdc1)
[ 1414.888000]     fat_get_cluster: invalid cluster chain (i_pos 0)
____________________________________________________________________________________

I have tried unmounting it (because the filesystem, from what I gather) won't allow changes to the device if it is presently in use, which it would be through the automounter. However I can't umount the device because it is "busy".

Any ideas or suggestions?

(and just on a note, the iAudio keeps its firmwhere ON THE DRIVE, in a user accessible area, so I am reticient to just gpart the damn thing, but will give it a try if necessary)

---

### Post by optimus.prime on 2007-09-08
Okay, as an update, I have also tried fsck'ing the unmounted device, still with no luck. Any suggestions, or would the majority say I've borked it?

---

### Post by drlouis on 2007-09-19
I'm experiencing a similar issue with a generic brand mp3 player.  Mine occurred when the system froze (an intermittent  problem I've experienced with 7.04) after writing a playlist to the device, but before I was able to umount it.  I'd love to find a solution.  

I booted into windows which reports the device as not formatted, and offers to format it for me.  Thus far I've declined.

---

### Post by 7he on 2008-01-16
Try this:
sudo dosfsck -a /dev/sda2

It fixed the problem for me. I had the error described above on an iPod nano 3g.

---

### Post by naaman on 2008-02-18
> **7he said:**
> Try this:
sudo dosfsck -a /dev/sda2

It fixed the problem for me. I had the error described above on an iPod nano 3g.

Spot on. Thanks dude.

I have posted the fix on ErrorsIGet ;) -> [http://errorsiget.meard.org/index.php?title=Fat32-FilesystemPanic](http://errorsiget.meard.org/index.php?title=Fat32-FilesystemPanic)

---

