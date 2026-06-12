---
title: "[SOLVED] howto change MDADM UUID / superblock , &amp;quot;superblock on /dev/nnn doesn't match"
date: 2007-04-15
forum: General Help
---

### Post by djamu on 2007-04-15
After switching my server from 6.06 > 7.04 ( i'm skipping 6.10 because of broken sata_uli with M5281 chipset )  to support my new hardware ( sata_mv + fixed sata_uli on 2.6.20 kernel )

To be on the safe side I removed my RAID 
clean installation of 7.04 +complete update + mdadm install ( before attaching any raid disk )
halt
attached raid array
boot 

array is raid 5 with 4 disks, previously I removed 1 disk
array was temporary running in degraded mode ( which should have been fine )

array refuses to assemble 
```

root@ubuntu:/# mdadm --assemble /dev/md0 /dev/hdg1 /dev/hdh1 /dev/sda1
mdadm: superblock on /dev/sda1 doesn't match others - assembly aborted

```

brought array back to 6.06 server, same result.... so this means :evil: 7.04 wrote something on /dev/sda1, without noticing or consulting me - it wasn't even mounted, doesn't exist in fstab, I always mount manually -

it's similar ( yet different ) from my previous post 
[http://ubuntuforums.org/showthread.php?t=405782&highlight=mdadm]("http://ubuntuforums.org/showthread.php?t=405782&highlight=mdadm")

```

root@ubuntu:/# mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.03
           UUID : 8d754c1d:5895bb70:**[COLOR="Red"]b1e8e808:894665ea[/COLOR]**
  Creation Time : Sun Sep 10 22:51:43 2006
     Raid Level : raid5
    Device Size : 156288256 (149.05 GiB 160.04 GB)
     Array Size : 468864768 (447.14 GiB 480.12 GB)
--------snipsnip
-
/dev/hdg1:
          Magic : a92b4efc
        Version : 00.90.03
           UUID : 8d754c1d:5895bb70:**[COLOR="Red"]c89ffdee:815a6cef[/COLOR]**
  Creation Time : Sun Sep 10 22:51:43 2006
     Raid Level : raid5
    Device Size : 156288256 (149.05 GiB 160.04 GB)
     Array Size : 468864768 (447.14 GiB 480.12 GB)
-------snipsnip
-
/dev/hdh1:
          Magic : a92b4efc
        Version : 00.90.03
           UUID : 8d754c1d:5895bb70:**[COLOR="Red"]c89ffdee:815a6cef[/COLOR]**
  Creation Time : Sun Sep 10 22:51:43 2006
     Raid Level : raid5
    Device Size : 156288256 (149.05 GiB 160.04 GB)
     Array Size : 468864768 (447.14 GiB 480.12 GB)

root@ubuntu:/# mdadm --assemble /dev/md0 /dev/hdg1 /dev/hdh1 /dev/sda1
mdadm: superblock on /dev/sda1 doesn't match others - assembly aborted

```

while the hdh1 and hdg1 drive are ok, the UUID / superblock for sda ( and the removed sdb ) changed.

How do I fix this ?

guess here goes my sunday afternoon.

Thanks alot !

---

### Post by djamu on 2007-04-24
OK. resolved this, 

Don't know ( yet ) how this happened, but seems like you can re-create your array
( tested this first with dummy arrays on vmware )

_**Use 1 missing device when defining the array to make sure it doesn't start (possibly wrong )  resyncing**_

It's very important to define the EXACT sequence your array previously was in ( make sense as it then finds it's spare blocks where they where before ), 
do: 
mdadm -E  /dev/sda1 ( or whatever device + partition your using ) and this for any device in the array
```

root@feisty-server:/# mdadm -E /dev/sda1

----snip

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        [COLOR="DarkOrange"]0[/COLOR]     active sync   /dev/sda1
   1     1       0        0         [COLOR="DarkOrange"]1[/COLOR]      faulty removed
   2     2      22        1         [COLOR="DarkOrange"]2[/COLOR]      active sync   /dev/hdc1
   3     3      22       65         [COLOR="DarkOrange"]3[/COLOR]      active sync   /dev/hdd1


```
and then do 
```

mdadm --create /dev/md0 --assume-clean --level=5 --raid-devices=4 /dev/sda1 [COLOR="Sienna"]missing[/COLOR] /dev/hdc1 /dev/hdd1

```

it gave me some info about the previous state of the array, and asked me if I really wanted to continue > Yes

mounted it & voila it worked again :) 

( tested this on vmware without the "--assume-clean" flag, and even with --zero-superblock, but I didn't dare to do this with my real array - guess that should be ok-

if you give the wrong sequence > 

 /dev/sda1 missing /dev/hdd1 /dev/hdc1 
or 
 /dev/sda1 /dev/hdc1 /dev/hdd1 missing


the array will still be created but will refuse to mount, DO NOT RUN  FSCK on the MD device as it will definetly kill your data. Just try again with another sequence 
( the underlying physical device blocks have actually nothing to do with the actual filesystem of the MD device )
As I was studying the subject, I noticed that there's a lot of confusion regarding the MD superblocks, just keep in mind that both the physical device (as part of the array ) & the MD device ( the complete array with filesystem ) have superblocks....

**Mount your array & check the contents before adding the missing disk**

[B]when your array works, don't forget to add the missing disk ( the one not used while reassembling the array ) using following command use the correct MD- & disk device 

don't copy & paste !!!

[/B]

```
mdadm /dev/md0 -a /dev/hda1
```



hope it helps someone.

---

### Post by Gruelius on 2007-04-29
That worked for me however after i rebooted mdadm tells me that it cant find any of the devices.
```

julius@tuxserver:~$ sudo mdadm --assemble /dev/md0
mdadm: no devices found for /dev/md0

```
```

julius@tuxserver:~$ sudo mdadm -E /dev/hdb/dev/hdb:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : daf47178:4eba9cde:1ed6dcb2:94163062
  Creation Time : Sun Apr 29 15:55:56 2007
     Raid Level : raid5
    Device Size : 195360896 (186.31 GiB 200.05 GB)
     Array Size : 781443584 (745.24 GiB 800.20 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Sun Apr 29 18:31:17 2007
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 1dd6f07c - correct
         Events : 0.12

         Layout : left-symmetric
     Chunk Size : 128K

      Number   Major   Minor   RaidDevice State
this     0       3       64        0      active sync   /dev/hdb

   0     0       3       64        0      active sync   /dev/hdb
   1     1      33        0        1      active sync   /dev/hde
   2     2      33       64        2      active sync   /dev/hdf
   3     3      34        0        3      active sync   /dev/hdg
   4     4      34       64        4      active sync   /dev/hdh

```

and then
```

julius@tuxserver:~$ sudo mdadm --assemble /dev/md0 /dev/hdb /dev/hde /dev/hdf /dev/hdg /dev/hdh
mdadm: superblock on /dev/hde doesn't match others - assembly aborted

```


..sigh.. any ideas?

---

### Post by djamu on 2007-04-30
> **Gruelius said:**
> That worked for me however after i rebooted mdadm tells me that it cant find any of the devices.
```

julius@tuxserver:~$ sudo mdadm --assemble /dev/md0
mdadm: no devices found for /dev/md0

```
```

julius@tuxserver:~$ sudo mdadm -E /dev/hdb/dev/hdb:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : daf47178:4eba9cde:1ed6dcb2:94163062
  Creation Time : Sun Apr 29 15:55:56 2007
     Raid Level : raid5
    Device Size : 195360896 (186.31 GiB 200.05 GB)
     Array Size : 781443584 (745.24 GiB 800.20 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Sun Apr 29 18:31:17 2007
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 1dd6f07c - correct
         Events : 0.12

         Layout : left-symmetric
     Chunk Size : 128K

      Number   Major   Minor   RaidDevice State
this     0       3       64        0      active sync   /dev/hdb

   0     0       3       64        0      active sync   /dev/hdb
   1     1      33        0        1      active sync   /dev/hde
   2     2      33       64        2      active sync   /dev/hdf
   3     3      34        0        3      active sync   /dev/hdg
   4     4      34       64        4      active sync   /dev/hdh

```

and then
```

julius@tuxserver:~$ sudo mdadm --assemble /dev/md0 /dev/hdb /dev/hde /dev/hdf /dev/hdg /dev/hdh
mdadm: superblock on /dev/hde doesn't match others - assembly aborted

```


..sigh.. any ideas?

sure, 

sidenote not really relevant but worth the info:
 > it seems that your not using partitions ( not that it matters much ) but since there's no partition table, other OS's ( M$ ) might write something ( initialize ) on it destroying at least a couple of sectors -as I said not really relevant if those disks never see windows, but still good practice to use partitions-

```
sudo mdadm -E /dev/hdb/dev/hdb
```
on the beginning is probably a typo right?

just do this for any hd ( and post )
it's very probable that some drive letters changed name ( ex. /dev/hdf that became /dev/hdi )
assembling them with the old drive names won't work in that case. 
( got an earlier post about that here 
[http://ubuntuforums.org/showthread.php?t=405782]("http://ubuntuforums.org/showthread.php?t=405782")
This happened after I inserted a removable drive + reboot while it was inserted.
It didn't happen again since then ( did you recently do a system upgrade, if yes chances are that MDADM got upgraded to ..... )

an example:
note: examining /dev/hdc1 gives a result for /dev/hdg1 
I've put it in red. Read this as follows " The device /dev/hdc1 formerly known as /dev/hdg1 "

```

root@ubuntu:/# [COLOR="Red"]mdadm -E /dev/hdc1[/COLOR]
/dev/hdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 23d10d44:d59ed967:79f65471:854ffca8
  Creation Time : Mon Apr  9 21:21:13 2007
     Raid Level : raid0
    Device Size : 0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1

    Update Time : Mon Apr  9 21:21:13 2007
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 2e17ac36 - correct
         Events : 0.1

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0      34        1        0      active sync   [COLOR="Red"]/dev/hdg1[/COLOR]

   0     0      34        1        0      active sync   /dev/hdg1
   1     1      34       65        1      active sync   /dev/hdh1


```

To make a long story short. Do a #mdadm -E for all devices, write down their current & old names & make a table [ raid device nr. / new name / old name ]

- if all UUIDs ( of the physical device !, not the MD device ) match, just assemble it using the new names ( use the raid device nr. to define the correct sequence )

- if UUID's differ, recreate using new names & raid device nr for correct sequence ( use 1 missing, so your array doesn't start resyncing & possibly wiping a wrong assembled array, if everything is fine and your able to mount it, you can re-add the missing disk )

If in doubt just ask again, I'll give you the correct command

good luck

---

### Post by DannyW on 2007-05-12
Hello. Nice how to, but unfortunately the UUID's are messed up again after rebooting.

I posted a thread earlier today before I found yours:
[http://ubuntuforums.org/showthread.php?t=441040](http://ubuntuforums.org/showthread.php?t=441040)

Basically, I want to set up a raid5 array consisting of sda1(500GB), sdc1(500GB) and md0(raid0:200GB300GB).

The raid0 array (/dev/md0) created fine. When creating the raid5 array (/dev/md1) it initally started as a degraded, rebuilding array, which is normal for raid5. After a couple of hours when this had finished the raid5 array looked normal.

After rebooting it initialised with just 2 drives. I could fix this by mdadm --manage /dev/md1 --add /dev/md0, then after a couple of hours of rebuilding it was fine again. Until the reboot.

After reading this thread I noticed the UUID's given by mdadm --misc -E /dev/sda1 /dev/sdc1 /dev/md0 were not all the same. md0 was different; it was the same as the UUID's of the devices of the raid0 array, /dev/md0.

So I used your method. The /dev/md1 was mountable with /dev/md0 missing, and so I knew it was safe to add /dev/md0 to the array. I did this and then after a couple of hours the array looked fine.

I rebooted, and now sda1 and md1 share the UUID of the devices in the raid0 array, and sdc1 has a unique UUID.

I hope I have explained this clearly enough.

Any help would be greatly appreciated!

Thank you.

```
danny@danny-desktop:~$ cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=2ef71727:a367450b:4f12a4b2:e95043a1
ARRAY /dev/md1 level=raid5 num-devices=3 UUID=4c4b144b:ae4d69bc:355a5a07:0f3721ab


# This file was auto-generated on Fri, 11 May 2007 18:08:52 +0100
# by mkconf $Id: mkconf 261 2006-11-09 13:32:35Z madduck $

danny@danny-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# /dev/sda3
UUID=99873af1-7d82-476c-975e-7165fedb7cee       /               ext3            defaults,errors=remount-ro      0       1
# /dev/sda1
UUID=56703a2b-449e-4c73-b937-41e5de341a0d       /boot           ext3            defaults                        0       2
/dev/mapper/vghome-lvhome                       /home           reiserfs        defaults,nodev,nosuid           0       2
# /dev/sda2
UUID=801702de-257d-481b-b0de-9ad2108893da       none            swap            sw                              0       0
/dev/scd0                                       /media/cdrom0   udf,iso9660     user,noauto                     0       0
proc                                            /proc           proc            defaults                        0       0
```


Note: I noticed during boot there was a message:
"mdadm: no devices listed in conf file were found"

Also, I'm using LVM2, though I doubt this is related. /dev/md1 is the only PhysicalVolume in my LVM VolumeGroup.

---

### Post by djamu on 2007-05-12
> **DannyW said:**
> 
Basically, I want to set up a raid5 array consisting of sda1(500GB), sdc1(500GB) and md0(raid0:200GB300GB).


mmm, interesting but according to me doomed to work consistently.
Why ?
For MD1 to work MD0 has to be completely assembled first, otherwise MD1 will start with 1 device missing ( MD0 )
Since you won't benefit  ( speed wise ) from that stripe ( remember RAID5  is also a stripe, actually RAID0 + parity ) because your actual speed depends on the slowest device. ( like an internet connection ).

Guess the idea was to have raid 5 with 3 * 500 gb devices
Because of the speed issue I mentioned before. It would work equally good with a linear raid.
which does the same thing as a LVM / EVMS volume.... I prefer using EVMS whenever I can, since this has a lot  more options  -  if your using a desktop ( Gnome ? ) there is a nice GUI in the repository.

In your case you'll have to stick with LVM because EVMS doesn't have kernel support ( yet )-  I might be wrong on this one regarding the new feisty kernel -

So instead of using a raid0 for the 2 drives ( 200 + 300 ) use LVM to built a 500 gb device and use that one for your RAID5

A workaround would be to remove your MD1 device from your mdadm.conf to make sure MD0 gets assembled properly before assembling MD1 manually ( script this :)   ) ...... not very handy, but doable...

> 
After rebooting it initialised with just 2 drives. I could fix this by mdadm --manage /dev/md1 --add /dev/md0, then after a couple of hours of rebuilding it was fine again. Until the reboot.

So I used your method. The /dev/md1 was mountable with /dev/md0 missing, and so I knew it was safe to add /dev/md0 to the array. I did this and then after a couple of hours the array looked fine.

I rebooted, and now sda1 and md1 share the UUID of the devices in the raid0 array, and sdc1 has a unique UUID.


What method ? :) , like I said before there's no way to tell what device gets assembled first. use LVM for your third RAID5 device.

> 
Note: I noticed during boot there was a message:
"mdadm: no devices listed in conf file were found"


Just ignore this. ( your on Feisty right ? ) It has something to do with the new MDADM version.
For your info - & contrary to what the manual says - you don't need mdadm.conf ... 
( actually it depends on the mode mdadm is running ), your arrays will be assembled as soon as the mdadm kernel module detects them. 
None of my servers has a mdadm.conf ( allthough I must tell you, that those only run dapper & edgy ), 
nor does the arrays appear in fstab because I prefer to manually ( some cron scripts ) mount them.
I got a feisty Desktop ( with raid ) which has a automatically generated mdadm.conf, didn't check if you can delete this. Dapper / Edgy & Feisty use all different versions of MDADM ( dapper v 1.xx -got to check this- edgy & feisty v 2.xx )

> 
Also, I'm using LVM2, though I doubt this is related. /dev/md1 is the only PhysicalVolume in my LVM VolumeGroup.


huh ?   mmmm...   maybe you better post following, ... you made a LVM volume out of the  RAID volume.
use EVMS instead. way more options, and since it doesn't run ( yet ) at boottime....

```

fdisk -l

cat /proc/mdstat


```


( I'll have to check some things, so expect this reply to get altered )

cheers

Jan

---

### Post by DannyW on 2007-05-13
Wow! Thank you very much for the informative and speedy reply!

The only reason I used LVM on the raid5 was so that I could extend the volume if I ever needed to. But I see this can be done easily with mdadm, which makes more sense. I just wasn't sure if it was possible to remove LVM whilst keeping my data safe, so just left it in place.

Using LVM for the raid0 makes perfect sense, and I assume this can be done without losing data, as the raid 5 can run degraded whilst I set up the 3rd device.

Would there then be issues with which starts first, LVM or mdadm?

Some good news is, I again used information from your earlier post to stop the array and recreate it and, for now, all is working ok.

I stopped the arrays (this time both of them, previously I only did the raid5), zeroed the super blocks and recreated with the same device order.

```
mdadm --manage /dev/md1 --stop
mdadm --manage /dev/md0 --stop
mdadm --zero-superblock /dev/sdb1
mdadm --zero-superblock /dev/sdd1
mdadm --zero-superblock /dev/sda1
mdadm --zero-superblock /dev/sdc1
mdadm --zero-superblock /dev/md0
mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/sdb1 /dev/sdd1
mdadm --create /dev/md1 --level=5 --raid-devices=3 /dev/sda1 /dev/sdc1 /dev/md0
```

After the couple hour rebuild things are ok, I haven't rebooted many times since I completed this step, so I'm not very confident about it holding up.

Meanwhile, I shall do some research on EVMS, to see what it can offer me.

I can switch md0 over to LVM easily, but I don't know if I can remove LVM, keeping my data in place, I'll try to find some info on this too.

Once again, thank you for that great response! I may be back in touch very soon when it breaks ;)

Kind regards,
Danny

---

### Post by djamu on 2007-05-13
np.
It won't break that easy, as long as it runs. :lol:.

Moreover, one of the problems I had lately was that my linux still recognized a reiserFS on a full ( not quick ! ) formatted NTFS ( which had reiserFS before ). 
Needed to zero "dd" the first GB's ( didn't have the patience to do a full zero dd )
[http://ubuntuforums.org/showthread.php?t=422549]("http://ubuntuforums.org/showthread.php?t=422549")
It's actually quite assuring these things are so persistent  :-\" 

Just make sure you post your results, others might benefit from it to.


Jan

---

### Post by Rexxars on 2008-01-09
Hi

Sorry to dig this up from the grave, but I've got a related problem and I'm desperate to find some solutions.

I moved all the disks in my RAID5 array from one faulty computer to a new computer running the same debian setup. Obviously the devices got juggled around a bit, and after reading this thread I tried to recreate it using the method mentioned above (mdadm -E and noting down the sequence).

Unfortunately, my sloppy fingers missed a "1" on the last devices, so it said mdadm --create <snip> /dev/sdg1 /dev/sdh
Now I'm getting a "Cannot open /dev/sdh1: No such file or directory" error! Am I doomed, or is there some way to fix this?

---

### Post by djamu on 2008-01-09
wow 2,326 page views, seems I wasn't the only one having some issues.

> Unfortunately, my sloppy fingers missed a "1" on the last devices, so it said mdadm --create <snip> /dev/sdg1 /dev/sdh
Now I'm getting a "Cannot open /dev/sdh1: No such file or directory" error! Am I doomed, or is there some way to fix this?


K don't worry

**Assuming the array was fully functional**
You did recreate using a missing drive isn't it ? ( to avoid a possibly wrong resync )

1.You did manage to mount the array.
If so then your partition table got destroyed but that has nothing to do with the MD device... so be it... ignore it.. ( if your array is fully resynced you can remove this disk, repartition it and add it again 

2.you didn't manage to mount the array. 
since I assume the array was ok before you moved it -all drives working- just reassemble the array with this disk missing ( /dev/sdh = missing ) & all should be ok

mount the array ( before adding the missing disk ) to make sure it's readable 
repartition /dev/sdh and add it to the array ( it will start resyncing as soon as you add it. no need to dismount it ( it's called redundancy :)

if you're unsure PM me with your email adres... if you want I can do all steps for you thru an ssh session ( I know it's a matter of thrust, but I can assure you i'm doing this on a daily basis.... )

if not provide me with some more info ( read previous posts carefully & completely ), and most important **DO NOT RUN FSCK** on individual disks or MD devices as it will definately kill your data.

Jan

---

### Post by Rexxars on 2008-01-10
> **djamu said:**
> 
**Assuming the array was fully functional**
You did recreate using a missing drive isn't it ? ( to avoid a possibly wrong resync )

I did not recreate using a "missing" drive, didn't understand what that ment, and felt confident I could do it without (silly me), **however**, I ran cat /proc/mdstat after it was "assembled" and I didn't find anything fishy (rebuilding etc)

> **djamu said:**
> 
1.You did manage to mount the array.
If so then your partition table got destroyed but that has nothing to do with the MD device... so be it... ignore it.. ( if your array is fully resynced you can remove this disk, repartition it and add it again 

I believe it did succeed, so it probably ruined the partition table, yes.

> **djamu said:**
> 
if you're unsure PM me with your email adres... if you want I can do all steps for you thru an ssh session ( I know it's a matter of thrust, but I can assure you i'm doing this on a daily basis.... )

I'll send you a private message, if I can get some help from a person who knows what he's doing, that's usually the best choice ;)

Thanks in advance.

---

### Post by numen101 on 2008-02-24
Rexxars and djam, what was the outcome of this issue..

I'm in a situation where I've moved my raid5 drives to a new machie, where I've tried to recreate the array with mdadm -C with what I think is the right sequence of drives (and I've tried different sequences).

I have LVM on top of the raid device, where the issue is that the raid5 array seems ok as does the LVM volume, but the LMV volume won't mount.

Any pointers on this would be appreciated..

Jesper

---

### Post by djamu on 2008-02-24
> **numen101 said:**
> Rexxars and djam, what was the outcome of this issue..

I'm in a situation where I've moved my raid5 drives to a new machie, where I've tried to recreate the array with mdadm -C with what I think is the right sequence of drives (and I've tried different sequences).

I have LVM on top of the raid device, where the issue is that the raid5 array seems ok as does the LVM volume, but the LMV volume won't mount.

Any pointers on this would be appreciated..

Jesper

Hi

K first of all did you reassemble it with a "missing" ( meaning using the statement missing ) like this
```
mdadm --create /dev/md0 --assume-clean --level=5 --raid-devices=4 /dev/sda1 [COLOR="Lime"]missing[/COLOR] /dev/hdc1 /dev/hdd1
```

A "missing" isn't a drive that's removed, missing is just a statement for a possible existing drive....
using that statement prevents the array from a possible wrong resync.....
all devices use their own superblocks... so the superblocks of the array are written on individual disks devices, LVM superblocks on the MD device, FS superblocks on the LVM device... ( note that a FS can reside directly on a MD device, in almost any combination )

second, did your array use a standard ( 64kB ) block size > in other words did you NOT specify a custom blocksize when creating the array for the first time -maybe I should contact the authors of those howto's urging users to use custom blocksize's for ... gee I've no idea actually, because this will only cause troubles when recreating, especially when done by a different person-

post 
```
mdadm -E /dev/sda1
```
for all drives ( check if you where using partitions, it's not really necessary to do, but good practice)

post ALL commands you previously issued, so I know what you did ...

I'll be around here for some time...

---

### Post by numen101 on 2008-02-24
> **djamu said:**
> Hi

K first of all did you reassemble it with a "missing" ( meaning using the statement missing ) like this
```
mdadm --create /dev/md0 --assume-clean --level=5 --raid-devices=4 /dev/sda1 [COLOR="Lime"]missing[/COLOR] /dev/hdc1 /dev/hdd1
```

A "missing" isn't a drive that's removed, missing is just a statement for a possible existing drive....
using that statement prevents the array from a possible wrong resync.....
all devices use their own superblocks... so the superblocks of the array are written on individual disks devices, LVM superblocks on the MD device, FS superblocks on the LVM device... ( note that a FS can reside directly on a MD device, in almost any combination )

second, did your array use a standard ( 64kB ) block size > in other words did you NOT specify a custom blocksize when creating the array for the first time -maybe I should contact the authors of those howto's urging users to use custom blocksize's for ... gee I've no idea actually, because this will only cause troubles when recreating, especially when done by a different person-

post 
```
mdadm -E /dev/sda1
```
for all drives ( check if you where using partitions, it's not really necessary to do, but good practice)

post ALL commands you previously issued, so I know what you did ...

I'll be around here for some time...

Thanks for your quick reply djamu,

I think I may have created the array without a missing drive as I wasn't aware of the potential danger.
But I've recreated it several times using different drive sequences using a missing drive all with a 64K chunk size as when the array was originally created.
```
[root@localhost ~]# mdadm -E /dev/sda4
/dev/sda4:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 0af0af63:20e2bf3d:76667f19:6c1bf312
  Creation Time : Sun Feb 24 14:38:16 2008
     Raid Level : raid5
    Device Size : 241858496 (230.65 GiB 247.66 GB)
     Array Size : 725575488 (691.96 GiB 742.99 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sun Feb 24 14:38:16 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 556fab2a - correct
         Events : 0.1

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        4        0      active sync   /dev/sda4

   0     0       8        4        0      active sync   /dev/sda4
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       0        0        3      faulty

[root@localhost ~]# mdadm -E /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 0af0af63:20e2bf3d:76667f19:6c1bf312
  Creation Time : Sun Feb 24 14:38:16 2008
     Raid Level : raid5
    Device Size : 241858496 (230.65 GiB 247.66 GB)
     Array Size : 725575488 (691.96 GiB 742.99 GB)
   Raid Devices : 4

[root@localhost ~]# mdadm -E /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 0af0af63:20e2bf3d:76667f19:6c1bf312
  Creation Time : Sun Feb 24 14:38:16 2008
     Raid Level : raid5
    Device Size : 241858496 (230.65 GiB 247.66 GB)
     Array Size : 725575488 (691.96 GiB 742.99 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sun Feb 24 14:38:16 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 556fab4b - correct
         Events : 0.1

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       33        2      active sync   /dev/sdc1

   0     0       8        4        0      active sync   /dev/sda4
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       0        0        3      faulty

[root@localhost ~]# mdadm -E /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : bf22c579:109d1dd7:4c127066:39d7b9c8
  Creation Time : Sun Feb 17 22:26:21 2008
     Raid Level : raid5
    Device Size : 241866496 (230.66 GiB 247.67 GB)
     Array Size : 725599488 (691.99 GiB 743.01 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sun Feb 17 22:26:21 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 9cb25de7 - correct
         Events : 0.1

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       49        3      active sync   /dev/sdd1

   0     0       0        0        0      faulty
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1

  Total Devices : 4
Preferred Minor : 0

    Update Time : Sun Feb 24 14:38:16 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 556fab39 - correct
         Events : 0.1

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        4        0      active sync   /dev/sda4
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       0        0        3      faulty


```

Drive sdd1 has different superblock data as it was ignored as a missing drive when creating the array.
The array seems to be started and the LVM volume seems ok, but the issue is I can't mount the LVM volume as it's complaining a filesystem type wasn't given..

Jesper

---

### Post by djamu on 2008-02-24
> **numen101 said:**
> Thanks for your quick reply djamu,

snipsnip...

I think I may have created the array without a missing drive as I wasn't aware of the potential danger.
But I've recreated it several times using different drive sequences using a missing drive all with a 64K...

Jesper

mmm, K, your command line interface has a history... check this.. if you did reassemble with all drives & without the --assume-clean flag... chances are that your out of luck...
the fact that lvm seems ok doesn't necessarily mean it's ok.
Just as a sidenote > are you using snapshots on the LVM ? if not why are you using an LVM ? 

it's a bit silly that those things are not well - to not say completely un - documented.. but using a missing is crucial .... because the array will start resync as soon as you issue the create command ( without missing / --assume-clean )

I'm not saying your data is lost... but chances are rather high, I'm sorry to say I probably can't help you

same as for rexxars I might give it a go over a SSH session, PM me with the details then....

---

### Post by finite9 on 2008-05-14
it's so hard to find help for raid!  Not many sources apart from the wiki but that just gives a howto, not a full troubleshooting guide.  Anyway, I have an issue and wonder if you can help:

I setup RAID1, dmcrypt and LVM on 2.6.18 kernel with mdadm on 2 external eSATA 500GB discs that do not contain any filesystem needed for botting or using Linux; and it all worked beatifully until I rebooted.  Turns out kernel can only autodetect raid array if the superblock is at the beginning and I chose metadata format 1.0 instead of 0.9 or 1.1, which put it at the end of the disc/md device, wherever it puts it.

So, as I have only just set it all up and not even tested yet, nevermind put data on there, I want to wipe out the entire thing, start from scratch, but I cannot wipe it!! it is still being detected as an array.

I used badblocks with write test and test pattern random to wipe the first few hundred meg of the discs, I removed and repartitioned them both and set type to fd, removed mdadm.conf and rebooted.

Ran mdadm --create --verbose /dev/md0 --raid-devices=2 --level=raid1 /dev/sd[ab]1

to use the old superblock type and it said that they are already an array would I like to continue yes/no, but if I choose yes, it then proceeds to re-sync the array!!

--remove and --set-fail do not seem to remove them either.

I had not tried to --zero-superblock and will try this just as soon as my current dd operation is done.

Another weird thing...after attempting this wipe, I rebooted repartitioned and went to work, now when I ssh into the box, fdisk -l shows following:

```
[root@k2 ~]# fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          19      152586   83  Linux
/dev/hda2              20        9729    77995575   8e  Linux LVM

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

Disk [COLOR="Red"]/dev/md0[/COLOR]: 500.1 GB, 500105150464 bytes
2 heads, 4 sectors/track, 122095984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
[COLOR="Red"]
Disk /dev/md0 doesn't contain a valid partition table[/COLOR]
```

But it previously was the same as /dev/sda, the first 500GB disc, and reported as /dev/sdc.  Why is it now /dev/md0 with fdisk -l??  It wasn't like that even when I got the array working the first time before rebooting.

Now I cannot even dd sda1 as it says it's busy, so im dd'ing /dev/md0 and will then reboot to see if it fixes this issue.

---

### Post by SpaceBas on 2008-06-06
First, let me say THANK YOU - reading this thread has been very helpful and educational.

I recently upgraded from 7.10 to 8.04 (server) and lost my 2TB raid5 array... I had tried a lot of other mdadm commands, but at the end of the day it kept insisting that 2 of the drives had bad superblocks. 

The --zero-superblock command followed by a re-build of the array seems to be working. Its rebuilding as I write this.

I suspect it may be a result of the rebuild, but when I try and mount the raid I get the following error:
```
mount: unknown filesystem type 'ext4'
```
I'm aware that there is an ext4 in development, but I certainly did not use it when I formatted the array in Feb 07! 

Anyone have any ideas?

---

### Post by djamu on 2008-06-06
[SIZE="4"]TO Finite9[/SIZE]

Sorry I overlooked your question...

regarding this....
> 
Disk /dev/md0: 500.1 GB, 500105150464 bytes
2 heads, 4 sectors/track, 122095984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table


this is normal, I'll explain

for example > 
while /dev/sda1 is the first partition of device /dev/sda

/dev/md0 is NOT the first partition of /dev/md ( neither is dev/md1 )

/dev/md0 is a unpartitioned device in itself, like a -"superfloppy" memory stick- usb device that usually doesn't have partitions either and is  directly formatted...
And so it's telling you that it's missing a partition table on the device... nothing to worry about.

You can actually partition a raid device ( use > cfdisk /dev/md0 ON AN EMPTY ARRAY ! ) without the need of using LVM.

/dev/md0p1 is then the first partition of device /dev/md0
( like dev/sda1 is the first partition of device /dev/sda )

:guitar:

---

### Post by djamu on 2008-06-06
[SIZE="4"]TO SpaceBas[/SIZE]

> **SpaceBas said:**
> First, let me say THANK YOU - reading this thread has been very helpful and educational.

I recently upgraded from 7.10 to 8.04 (server) and lost my 2TB raid5 array... I had tried a lot of other mdadm commands, but at the end of the day it kept insisting that 2 of the drives had bad superblocks. 

The --zero-superblock command followed by a re-build of the array seems to be working. Its rebuilding as I write this.

I suspect it may be a result of the rebuild, but when I try and mount the raid I get the following error:
```
mount: unknown filesystem type 'ext4'
```
I'm aware that there is an ext4 in development, but I certainly did not use it when I formatted the array in Feb 07! 

Anyone have any ideas?

1st > What kind of FS was on it ? where those new disks ? ( linux filesystems can be very persistent ), if ever there was a different FS on there it might be recognized ( even if it was very briefly ).
Use a mount command -on the MD device :)- specifying the type ```
mount -t ext3/reiserfs/whatever .... 
```

you did rebuilt it using a missing device ( the statement ) ?
Be a little more specific > dump some info here ... saves time for me quessing...

:KS

---

### Post by SpaceBas on 2008-06-06
> **djamu said:**
> [SIZE="4"]TO SpaceBas[/SIZE]



1st > What kind of FS was on it ? where those new disks ? ( linux filesystems can be very persistent ), if ever there was a different FS on there it might be recognized ( even if it was very briefly ).
Use a mount command -on the MD device :)- specifying the type ```
mount -t ext3/reiserfs/whatever .... 
```

you did rebuilt it using a missing device ( the statement ) ?
Be a little more specific > dump some info here ... saves time for me quessing...

:KS
When the array was created in Feb 2007 the disks were brand new out of the box. The original array was formatted ext3.

I did *not* use the missing drive operator ... I rebuilt with all 4 (of 4) drives since two of them appeared to be fine. If that was a fatal mistake, then so be it...I've already come to grips with having lost the data. 

when  try to mount and specify the FS, I get: 
sudo mount -t ext3 /dev/md0 /local/media/
```
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

 Dmesg shows:```

[30341.197197] md: md0 stopped.
[30341.249009] md: bind<sdc1>
[30341.249166] md: bind<sdd1>
[30341.249320] md: bind<sde1>
[30341.249432] md: bind<sdb1>
[30341.292058] raid5: device sdb1 operational as raid disk 0
[30341.292061] raid5: device sde1 operational as raid disk 3
[30341.292064] raid5: device sdd1 operational as raid disk 2
[30341.292065] raid5: device sdc1 operational as raid disk 1
[30341.292383] raid5: allocated 4211kB for md0
[30341.292385] raid5: raid level 5 set md0 active with 4 out of 4 devices, algorithm 2
[30341.292387] RAID5 conf printout:
[30341.292388]  --- rd:4 wd:4
[30341.292390]  disk 0, o:1, dev:sdb1
[30341.292391]  disk 1, o:1, dev:sdc1
[30341.292393]  disk 2, o:1, dev:sdd1
[30341.292394]  disk 3, o:1, dev:sde1
[30344.109468] EXT3-fs: md0: couldn't mount because of unsupported optional features (4000000).

```

glad to post any thing else that may help - but not sure what that wold be

---

### Post by djamu on 2008-06-06
> **SpaceBas said:**
> 
snipsnip....
I did *not* use the missing drive operator ... I rebuilt with all 4 (of 4) drives since two of them appeared to be fine, If that was a fatal mistake, then so be it...I've already come to grips with having lost the data. .....


K well it most likely is fatal.... but just as a reminder..

> I rebuilt with all 4 (of 4) drives since two of them appeared to be fine >  

They where all fine .... it's just the UUID that is wrong....
The superblocks on the individual devices -superblocks on /dev/sdb /dev/sdc /dev/sdd /dev/sde-  have nothing to do with the superblocks of the raid array itself -dev/md0- .
in other words deleting superblocks on the individual disks ( the raid array superblocks )doesn't affect the superblocks from the array itself ( the FS superblocks )... if you add another layer - like LVM / EVMS - then this does also have it's own superblocks ... ( then you have 3 kinds of superblocks, 1 for each layer )...

In order to maintain consistency for the upper layer the lower layer needs to be assembled using the same RAID sequence ( I've explained this earlier ) & as long as it doesn't overwrite data ( rebuild ) you can infinitely retry assembling ( 4 disks gives you 24 possibilities )....

There's actually no need to erase the RAID superblocks in order to reassemble the array ( no harm either )...
BUT in order to correctly calculate the parity of the original data ( it can always create parity from whatever data ) using all 4 disks ( without the missing statement ) you have actually 1 chance out of 24  ( 1/24 > 2*3*4 ) that you got it right....

So it's very likely you've lost your data... It's too bad & I can't stress this enough **USE THE MISSING STATEMENT** A raid is meant to keep on working with 1 disk missing ( that is for a RAID5 ) for a **RAID6 you need 2 missing disk statements...** ( and it really doesn't matter which ones )

So I'm sorry that I can't help you.....

8-[

---

### Post by SpaceBas on 2008-06-06
> **djamu said:**
> K well it most likely is fatal.... but just as a reminder..


So I'm sorry that I can't help you.....

8-[

I appreciate your sincere response ...Like I said, I had already resigned myself to losing the data so at this point I'll just bookmark this thread and live and learn.

This is a very informative thread and had I followed it correctly I'm sure things would have been fine - learned a lot and that goes a long way.

---

### Post by finite9 on 2008-06-09
Ok, thanks for the tip.  I already figured out how to get my RAID1 working with dmcrypt.

Turns out that the sata_sil driver cannot handle standby with sil3512 chipsets so I have a cron job that keeps the drives alive. Dread to think what my electric bill is going to be next month.

---

### Post by cuervo73 on 2008-07-18
Hey finite9..

What exactly did you do in your cronjob to keep the mirror-slave drive from sleeping/spinning-down?

I have this same Sil 3512 controller with a pair of SATA drives setup as RAID 1 and when I don't write anything for awhile, the mirror-drive goes to sleep forcing the "sata_sil" driver to take measures to restart the drive.  This has the ugly side-effect of 90-100 seconds of system waiting for the drive to become ready again.

cuervo

---

### Post by djamu on 2008-07-19
> **cuervo73 said:**
> Hey finite9..
What exactly did you do in your cronjob to keep the mirror-slave drive from sleeping/spinning-down?....
cuervo

don't want to be rude but this is slightly off-topic 
people having to read unrelated info, especially since it's about lots of personal / company data ...

use PM or start a new thread, I'd be happy to help you there

):P

---

### Post by cuervo73 on 2008-07-20
Sure, djamu

mebbe you can help.. you see, I tried FIRST to send finite9 a private message asking that same thing you see here.. and this forum refused to send it replying that I needed 75 posts BEFORE I could send a PM!  Of all the lame, elitist settings in a forum, this takes the prize!  A forum is supposed to be setup to help, not obstruct, people asking questions.  So, I tried to ask my question in the P/C way, by not being off-topic, and using personal messaging but I wasn't able to do that.

I even considered going off to some obscure corner of the forum and posting some 70-odd dummy posting entries so that I could reach the 75 threshhold but rejected that because it was too lame.

So, I asked the poster for feedback and I managed to irk the OP which I tried not to in the first place.
</rant>

OK, so maybe you can alert finite9 that I have a query for him?

cuervo

PS: don't take my rant personally.. it is really directed to the forum gods.. I hope they read this one and realize how ARROGANT their 75 posting limit is!

---

### Post by djamu on 2008-07-20
> **cuervo73 said:**
> 
.. and this forum refused to send it replying that I needed 75 posts BEFORE I could send a PM!  Of all the lame, elitist settings in a forum, this takes the prize!....


You are absolutely right. The excuse is of-course that this is to prevent spam but since there's technology like Mollom server > an advanced invisible captcha that analyses text in it's context & sends a real captcha when in doubt ) this is quite lame. 

I'm not to keen on forumzombies either who post just to get their stats & credibility up.

---

### Post by cuervo73 on 2008-07-20
I don't post here fundamentally b/c I'm not using Ubuntu anymore.. too many issues.  There are too many other distros which have it together, aren't elitist, and just plain work.. like RHEL/CentOS, (older)Fedoras, OpenSuSE, Mandriva,  and Debian.

I only posted here this time b/c I googled for Sil3512 and this thread was google-indexed, so I came over to see what was posted about that chipset/driver.

thanks, bud!

cuervo

---

