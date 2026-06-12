---
title: "raid5 wont mount on start"
date: 2008-01-30
forum: General Help
---

### Post by breaking on 2008-01-30
upon restarting my server the raid5 array fails to mount. my mdadm.conf and fstab seem to be correct but every time i restart i need to reassemble and mount the array. can you see an issue?
> 
mdadm -A /dev/md0
mdadm: no devices found for /dev/md0
mdadm -A /dev/md0 /dev/sd[abcd]1
mdadm: /dev/md0 has been started with 4 drives.
mount -a
mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Fri Dec 14 14:05:34 2007
     Raid Level : raid5
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Jan 30 21:24:50 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : cef09fa8:69565cd3:bc08ddf6:b77fa3ff
         Events : 0.2896

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1


> fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ef3e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/hda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b67c8ba

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       36132   290230258+  83  Linux
/dev/hda2           36133       36483     2819407+   5  Extended
/dev/hda5           36133       36483     2819376   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00018714

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c8136

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003f5c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

> # mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE /dev/sd[abcd]1

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=1fa07edc:7e281796:52d12144:c97b2cc4

# This file was auto-generated on Fri, 14 Dec 2007 13:59:01 -0600
# by mkconf $Id: mkconf 324 2007-05-05 18:49:44Z madduck $

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=02b9f6e9-acea-42a4-93ef-5f08e0354249 /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1
# /dev/hda5
UUID=36d170bd-81e6-464f-bd16-669099ab0bf0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/md0	/nfserver 	auto 	defaults 	0 	3

---

### Post by fjgaude on 2008-01-31
Everything looks okay to me except the fstab line:

```
/dev/md0 /nfserver auto defaults 0 3
```

That "3" should be a "2". But I'm not sure if that would stop the array from being mounted. Try changing to 2 and see.

You do have your mount point, /nfserver, made, eh?

Let us know how you make out.

---

### Post by breaking on 2008-01-31
i changed my fstab to reflect your advice and the issue persists.
> /dev/md0	/nfserver 	auto 	defaults 	0 	2

the directory /nfserver does exist and it mounts fine after i issue the commands to assemble and mount. it just refuses to do this automatically on startup. 

also, why a 2 instead of a 3 for the fstab?

---

### Post by fjgaude on 2008-01-31
The 2 checks the array's health as often as it checks the boot drive. The 3 does nothing, AFAIK.

I do believe your mount point may be the problem. Try something like /home/raid as the point and see what happens. Mounting off the root could just be the problem with a race issue.

We try, we try, and from all this we learn, day-by-day. <smile>

---

### Post by breaking on 2008-01-31
thanks for that tidbit.

i changed the mount point to /mnt/nfserver in my fstab and still had the same issue. its still not mounting on startup.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=02b9f6e9-acea-42a4-93ef-5f08e0354249 /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1
# /dev/hda5
UUID=36d170bd-81e6-464f-bd16-669099ab0bf0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
**/dev/md0	/mnt/nfserver 	auto 	defaults 	0 	2**

i still have to assemble and then mount it to gain access. could it have something to do with the fact that i have to reassemble it every time i restart? i am really not sure why that is happening.

> mdadm -A /dev/md0 /dev/sd[abcd]1
mdadm: /dev/md0 has been started with 4 drives.
mount -a

---

### Post by breaking on 2008-01-31
if i do not assemble it and just try to mount the array this is what i get:

> **mount /dev/md0**
mount: you must specify the filesystem type

i try and check things out with fsck:

> **fsck /dev/md0**
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext2: Invalid argument while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

then i assemble the array and then fsck it and this is what i get:

> mdadm -A /dev/md0 /dev/sd[abcd]1
mdadm: /dev/md0 has been started with 4 drives.
mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Fri Dec 14 14:05:34 2007
     Raid Level : raid5
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Jan 31 17:27:11 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : cef09fa8:69565cd3:bc08ddf6:b77fa3ff
         Events : 0.2896

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1

**fsck /dev/md0**
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Superblock has an invalid ext3 journal (inode 8).
**Clear<y>?** 


i stopped there because i am not sure what *clear* pertains to. will it wipe my data?
i could back up my data and try but that will take some time.

---

### Post by fjgaude on 2008-01-31
The only thing you are doing that seems somewhat strange to me, things which I've never done, is in your mdadm.conf file:

```
# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE /dev/sd[abcd]1
```

The [abcd] may not be recognized by the parsing that md goes through.

You could make that file into a backup, and then recreate the important aspects of the file with the usual command:

```
sudo echo &#8217;DEVICE /dev/hd*[0-9] /dev/sd*[0-9]&#8217; > mdadm.conf
sudo  mdadm --detail --scan >> mdadm.conf
```

You then have to copy from your home directory the mdadm.conf created to the /etc/mdadm folder.
If after rebooting the array doesn't auto come back, try doing this command:

```
sudo mdadm --assemble --scan
```

That way we know if everything is being read correctly as you boot up.

What we don't wish to do is anything that would cause the array to not function correctly, as you likely don't have a backup of the data on it, eh?

We will get to the bottom of this if we don't grow faint of heart. <smile>

---

### Post by breaking on 2008-01-31
well i backed up my mdadm.conf and issued the commands you suggested:
> echo ’DEVICE /dev/hd*[0-9] /dev/sd*[0-9]’ > mdadm.conf
 mdadm --detail --scan >> mdadm.conf

here is the new mdadm.conf: looks good.
> # mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=1fa07edc:7e281796:52d12144:c97b2cc4

# This file was auto-generated on Fri, 14 Dec 2007 13:59:01 -0600
# by mkconf $Id: mkconf 324 2007-05-05 18:49:44Z madduck $

restarted with the same persistent issue. still no mounting.

after restarting i issued your second recomended comand:

> mdadm --assemble --scan
**mdadm: no devices found for /dev/md0**


**note:** in the [_mdadm.conf man page_]("http://linux.die.net/man/5/mdadm.conf") it lists this under examples as a shorthand version:
Example
DEVICE /dev/sd[bcdjkl]1

that is where i got the idea. instead of writing out /dev/sdb1 /dev/sdc1 ...etc
although the tidbit of *echo* code comes in handy.

also, i seem to have a similar setup as you in respects to 4 large drives (4 x 500gb) in raid5. what exactly does one do with about a tb of data to backup? where to put those backups?

---

### Post by fjgaude on 2008-02-01
As far as backup, you either have tape or more drives on another box... Blu-ray DVDs. <smile>

I'm at a loss as to what is your problem... out of suggestions.

Good luck at whatever you decide.

---

