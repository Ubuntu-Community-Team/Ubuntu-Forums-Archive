---
title: "recover RAID-5 after OS reinstall"
date: 2012-12-04
forum: General Help
---

### Post by Forbees on 2012-12-04
last kernel update bricked my system so i had to reinstall. trying to get my softRAID-5 back up and running.


did pretty much everything from Gnome Disk Utility last time, but can't get it to recover


raid state "not running, partially assembled"
all drives are pluged in and say they're a part of the raid

clicking "check array"
```
Error checking array: helper exited with exit code 1: device /dev/md127 is not idle
```


saw a thread with a similar problem, adding a spare save him but when i tried
```
Error adding spare: mdadm exited with exit code 1: mdadm: cannot get array info for /dev/md127
```


blkid doesn't show /dev/md127
```
/dev/sda1: UUID="3361abb6-9e72-ac6a-7c4a-9256c12cffcc" UUID_SUB="d3061510-9250-9710-6531-2819ae38cef0" LABEL="Server-Data" TYPE="linux_raid_member" 
/dev/sdb1: UUID="3361abb6-9e72-ac6a-7c4a-9256c12cffcc" UUID_SUB="f3c14e1a-59fe-ae07-0403-3141f00aadcb" LABEL="Server-Data" TYPE="linux_raid_member" 
/dev/sdc1: UUID="3361abb6-9e72-ac6a-7c4a-9256c12cffcc" UUID_SUB="ddac997c-5629-cd51-8623-35712dd871d9" LABEL="Server-Data" TYPE="linux_raid_member" 
/dev/sdd1: UUID="8fc99913-1609-4d70-9be1-aa4b5be77302" TYPE="ext4" 
/dev/sdd5: UUID="62aa23cb-9f79-4fab-b9b8-e535d36d4381" TYPE="swap" 
```

my fstab might not be needed but here it is
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd1 during installation
UUID=8fc99913-1609-4d70-9be1-aa4b5be77302 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=62aa23cb-9f79-4fab-b9b8-e535d36d4381 none            swap    sw              0       0


```


mdadm.conf - where the problem probably is, but i don't know enough about it
```
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
ARRAY /dev/md/Server-Data metadata=1.2 UUID=3361abb6:9e72ac6a:7c4a9256:c12cffcc name=Server-Data

# This file was auto-generated on Tue, 04 Dec 2012 20:44:28 -0500
# by mkconf $Id$
```

---

### Post by Forbees on 2012-12-05
bump anyone? i have the data "backed up" . . . it's actually on a lost partition that i've taken an image of... so i can just start all new, but it takes about 6 days to copy it all over (data recovery is a pain lol) . .  


this is something i should be learning to do anyway so someone got an idea?

---

### Post by sciguy125 on 2012-12-06
It's been my experience that the system calls the array /dev/md127 when there's a problem with it (which is obviously the case).  See what you get for:

```
cat /proc/mdstat
```

and

```
mdadm --detail /dev/md127
```

I also want to mention that I recently had a problem with moving an array from one system to another (effectively the same as having to reinstall).  At the moment, I can't remember what was wrong or how I fixed it.  Hopefully, working through this with you will jog my memory.

---

### Post by Forbees on 2012-12-06
you sir are a knight - now lets jog that memory! :D

```

nagato@Yuki:~$ cat /proc/mdstat
Personalities : 
md127 : inactive sdb1[1](S) sdc1[0](S) sda1[3](S)
      5860142787 blocks super 1.2
       
unused devices: <none>

```

```

nagato@Yuki:~$ mdadm --detail /dev/md127
mdadm: must be super-user to perform this action
nagato@Yuki:~$ sudo mdadm --detail /dev/md127
[sudo] password for nagato: 
mdadm: md device /dev/md127 does not appear to be active.

```

also should mention so it doesn't come up later - acording to Gnome Disk Utility(GDU), the three drives are still a part of the raid - which i think cat /proc/mdstat has thankfully proven - and all three disks are "healthy", one of which with a few bad sectors, but still green

GDU still shows the raid in it, but it says a size of 0kb, and as stated in the first post "not running, partially assembled"

---

### Post by sciguy125 on 2012-12-06
Ok... mdstat tells us that the array has been assembled, but they're all spares for some reason.  Let's try disassembling the array, then assembling it again:

```
mdadm --stop /dev/md127
mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1
```

FYI, this is my mdadm reference: [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by Forbees on 2012-12-06
```
nagato@Yuki:~$ sudo mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.

```


being that it's set at spare, the data should still be there right? we just need to figure out how to tell at least two of them to stop being spares?

---

### Post by sciguy125 on 2012-12-07
It bothers me that it's not activating the "spares".  Does mdstat still say that they're all spares?

You might also want to verify that all the devices are still intact.  Specifically, make sure that the array UUID is the same for all of them and that they all look like they belong together:
```
mdadm --examine /dev/sda1 /dev/sdb1 /dev/sdc1
```

If you're brave enough to try it at this point, you can force it to start the array.  However, I'm not sure how smart it is.  If it hasn't been starting because it doesn't recognize that there's data, it might try to resync the array by wiping it.
```
mdadm --stop /dev/md0
mdadm --assemble --force /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1
```

---

### Post by Forbees on 2012-12-07
```
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 3361abb6:9e72ac6a:7c4a9256:c12cffcc
           Name : Server-Data
  Creation Time : Sun Nov 11 21:31:06 2012
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3906761858 (1862.89 GiB 2000.26 GB)
     Array Size : 3906760704 (3725.78 GiB 4000.52 GB)
  Used Dev Size : 3906760704 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : d3061510:92509710:65312819:ae38cef0

Internal Bitmap : 8 sectors from superblock
    Update Time : Fri Nov 30 11:50:05 2012
       Checksum : 4696f9e6 - correct
         Events : 74302

         Layout : left-symmetric
     Chunk Size : 1024K

   Device Role : Active device 2
   Array State : .AA ('A' == active, '.' == missing)
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 3361abb6:9e72ac6a:7c4a9256:c12cffcc
           Name : Server-Data
  Creation Time : Sun Nov 11 21:31:06 2012
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3906761858 (1862.89 GiB 2000.26 GB)
     Array Size : 3906760704 (3725.78 GiB 4000.52 GB)
  Used Dev Size : 3906760704 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : f3c14e1a:59feae07:04033141:f00aadcb

Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Dec  1 00:15:33 2012
       Checksum : 4accb5ba - correct
         Events : 74387

         Layout : left-symmetric
     Chunk Size : 1024K

   Device Role : Active device 1
   Array State : .A. ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 3361abb6:9e72ac6a:7c4a9256:c12cffcc
           Name : Server-Data
  Creation Time : Sun Nov 11 21:31:06 2012
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3906761858 (1862.89 GiB 2000.26 GB)
     Array Size : 3906760704 (3725.78 GiB 4000.52 GB)
  Used Dev Size : 3906760704 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : ddac997c:5629cd51:86233571:2dd871d9

Internal Bitmap : 8 sectors from superblock
    Update Time : Wed Nov 28 19:58:08 2012
       Checksum : 34fddfba - correct
         Events : 4969

         Layout : left-symmetric
     Chunk Size : 1024K

   Device Role : Active device 0
   Array State : AAA ('A' == active, '.' == missing)

```



forcing it might work, or might make me have to start over... lets brainstorm a couple more posts before trying it lol


edit: the examine is comforting me though. it apears that the RAID remembers i have data on it :D

---

### Post by sciguy125 on 2012-12-07
The most notable thing is that all the devices are out of sync.  The number of events are off and so are the update times.  In a healthy array, they would all be the same because all the devices should be updated at the same time.  (Though, I've never gotten a good answer as to what the event count is actually counting...)  If you had two drives that were synced, I would have recommended "recreating" the array using those two drives then adding the third drive afterwards.  Something similar to

```
mdadm --create /dev/md0 --assume-clean [...]
```

If I found myself in your situation, I would use --force at this point.  But, I'm a gambling man, so you may not have the same risk tolerance that I do.

If you want to do some reading, this is where I was going during my last raid recovery attempt:
[https://raid.wiki.kernel.org/index.php/Linux_Raid](https://raid.wiki.kernel.org/index.php/Linux_Raid)

---

### Post by Forbees on 2012-12-08
broken link is broken  :-/

so . .  should i try doing the assemble with only two drives and see what happens? (trying every combination of 2)

i'm about at the point of trying the force too, but if this happens again and, odds are i won't have my data half-assed backed up, so i'm not comfortable on a gamble unless we're sure it's the only way :-/



under the "array state:" section . .  i feel like that should be something to work off of. AAA .AA .A. i think they were. . . . shouldn't i be able to rebuild off of AAA and .AA ?

---

### Post by sciguy125 on 2012-12-08
There's no harm in trying, but it probably won't let you "assemble" the array using any combination of devices.  The reason it didn't want to do so with all three is that they're all out of sync.  Normally, it would assemble with as many as possible (that are in sync).

---

### Post by Forbees on 2012-12-09
did a  little more looking around and i'm pretty sure i need to do some config editing

```
nagato@Yuki:~$ sudo mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 --scan
mdadm: /dev/md0 not identified in config file.
mdadm: /dev/sda1 not identified in config file.
mdadm: /dev/sdb1 not identified in config file.
mdadm: /dev/sdc1 not identified in config file.

```


with that being said forcing it wouldn't work?

```

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
ARRAY /dev/md/Server-Data metadata=1.2 UUID=3361abb6:9e72ac6a:7c4a9256:c12cffcc name=Server-Data

# This file was auto-generated on Tue, 04 Dec 2012 20:44:28 -0500
# by mkconf $Id$
```

there's my conf again.... i noticed the device partitions containers area is empty. maybe i should be adding the drives there?

also, under array, shouldn't it be /dev/md0 instead of dev/md/Server-Data?

---

### Post by sciguy125 on 2012-12-09
My understanding is that mdadm.conf is only needed to autodetect arrays.  When you added --scan, it looked at mdadm.conf, didn't find the array, and told you so.  Once you fix the array, the only important line there would be the ARRAY line.  That ensures that your array will always get assigned to /dev/md0 instead of something that the init scripts choose.

You *could* explicitly add your devices to the DEVICE line, but they're already being picked up because it's scanning all partitions.

---

### Post by Forbees on 2012-12-09
what about the array not being called md0 in the conf?

---

### Post by sciguy125 on 2012-12-09
> **Forbees said:**
> what about the array not being called md0 in the conf?

You could change it to /dev/md0 if you want, but since you still can't get the array started manually, it won't matter at this point.

---

### Post by Forbees on 2012-12-11
k, so i couldn't figure anything else out so i finally decided to do the --force


and BAM all my data is there :D only one problem >,<


it started on only 2 of the 3 drives and is labeled "degraded" so i'm going to start playing around to figure out why one of the drives claims to be perfectly healthy, but not acting in the raid


Edit: using Gnome Disk Utility i found that one of the 3 drives wasn't "attached" so i clicked the attach button, now the drive appears to be recovering :D of all goes well this thread will be marked as solved in a half hour or less 


thanks a ton for your help

---

### Post by sciguy125 on 2012-12-11
Out of curiosity, which devices did it start with and which did you need to add manually?

Coincidentally, I just found this thread that appears to be a nearly identical problem:
[http://ubuntuforums.org/showthread.php?t=1652976](http://ubuntuforums.org/showthread.php?t=1652976)

---

