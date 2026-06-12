---
title: "[SOLVED] Large RAID Partition for a NAS"
date: 2008-06-26
forum: General Help
---

### Post by batfastad on 2008-06-26
Hi everyone

I have successfully installed a 3ware RAID card in our test server. It's set up as a RAID 6 using the 3ware BIOS RAID manager, with 5x500GB drives.
This gives me a capacity of around 1.4TB

The device is at /dev/sda and I've already played around creating a large partition on the device, but I want to make sure I get this absolutely right... before I fill it with data that will be difficult to move anywhere else.
I'm using Ubuntu Server 8.04 and I tried creating the partition with cfdisk, then formatting it as ext3 with mkfs. I can mount/umount fine and files appear to stay on there, for the moment ;)

I tried using the graphical GParted tool but it was giving me grief - I think because I was trying to create a partition >1TB in size

However I ran the sudo fdisk -l command to list all the partition information... I wanted to edit fstab to have the drive auto-mounted following the guide in a post on here.

But I get the following warning in fdisk for my RAID device at /dev/sda:
```
Disk /dev/sda: 1499.9GB, 1499968045056 bytes
255 heads, 63 sectors/track, 182360 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table
```
Then it goes on about /dev/sdb which is the main internal boot drive, but doesn't display such a warning for my 120GB boot drive.

Eventually I will be looking to add further drives to this array to increase the capacity to 2.5TB (there's 2 spare hot-swap bays in the backplane units we bought).
The 3ware card has some sort of online capacity expansion, but I worry that I'll have to re-partition.

So basically what's the best/most future proof way to create and then format large partitions over 1-2TB?

Should I just ignore that fdisk error?
Or is that something serious that needs looking at now?
Will the ext3 file system be ok for what I'm looking for?

Thanks, B

---

### Post by justleen on 2008-06-26
First off: no, you should not ignore that error of fdisk. No partitions are defined, any data stored on there will be written to a raw device. at this point you shouldnt be able to mount it as a partition (sdaX) anyway, only as a whole disk (sda).. which is not what you want.
YOu should really have a parition defined before going any further. 1TB shouldnt be a problem (for fdisk any way)
Try fdisk, or cfdisk. Or perhaps parted, instead of gparted.
Ext3 is fine for this.

Since you're planning on adding to the array, i'd suggest you'd use some kind of LVM on the array. this wil give you a lot more flexibilty on the partitions on the array, and will allow much easier resizing (expanding / shrinking existing partitions, instead of just adding new paritions).
If you have some free unpartitioned space, try playing around with a LVM on that..

Did you check the NAS allows adding disks (witout rebuilding the array)?

---

### Post by batfastad on 2008-06-26
Hi justleen, thanks for your quick reply!

I've been testing the device by mounting /dev/sda, which is incorrect.
So if there was a valid partition, I would actually need to be mount /dev/sda1
Thanks for clearing that up - that's what I was worried about.

I did try using cfdisk to create the partition... but clearly it wasn't created correctly!
I'll try fdisk instead to see if I have any luck.

I just wasn't sure how "legacy" fdisk was... whether it was written in the 80s and didn't support volumes greater than 2KB or something ;)
I thought there might be a more modern utility. I'll have another go with cfdisk, then try fdisk.

Good news that ext3 is an ok filesystem to use for this.

The 3ware RAID controller I've got is a 9690SA 8I... 8 port multi-lane internal SATA/SAS
If I add drives, I think I will need to tell the controller to rebuild the array onto those drives. But it will handle all that automatically.
Then I guess it's a case of somehow resizing that one big partition.

Thanks for your help ;)

---

### Post by justleen on 2008-06-26
[check out this wiki for some details on ext3]("http://en.wikipedia.org/wiki/Ext3fs") there is a section on filesystem limits.

Normally, adding a disk to a raid will not resize the parition! It will give you more space - available for partitioning.
eg. if you have 5 disks in an array, total 5GB with one 1GB partition, and you add a disk, the array will be rebuild, ending up with 1GB partition, and another 5GB avail for paritioning. To expand the 1GB parition, you will have to resize that.
The RAID controllor will just "spread" the existing parition over the available disks (im not talking bout spares in this case).

as an LVM example: say you have 10 partitions on 5 disks, each 10GB (totalling 100GB on 5 disks). 
LVM will allow you to group these disks/paritions in a Logical volume group.
Within this LVG, you can create logical volumes. so you could create 2 paritions each 25GB, which the OS will see. these 2 partitions will be all over the 10parts/5 disks
If you run out of space, you can simply resize a LVM. 
adding a disk allows you to add it to the LVG, which is then available to expand existing LVM's or create new LVM's...

hope that make sense ;)

other example, a disk:
fdisk:
```

           Device Boot      Start         End      Blocks   Id  System
/dev/cciss/c0d0p1   *           1         261     2096451    6  FAT16
/dev/cciss/c0d0p2             262         274      104422+  83  Linux
/dev/cciss/c0d0p3             275        3917    29262397+  8e  Linux LVM



```mount -l:```

/dev/sda1 on /data1 type ext3 (rw) [
/dev/mapper/lvm_main-root on / type ext3 (rw) []
/dev/cciss/c0d0p2 on /boot type ext3 (rw) [/boot]]
/dev/mapper/lvm_main-home on /home type ext3 (rw) []
/dev/mapper/lvm_main-opt on /opt type ext3 (rw) []
/dev/mapper/lvm_main-tmp on /tmp type ext3 (rw) []
/dev/mapper/lvm_main-usr on /usr type ext3 (rw) []
/dev/mapper/lvm_main-usr.local on /usr/local type ext3 (rw) []
/dev/mapper/lvm_main-var on /var type ext3 (rw) []
/dev/mapper/lvm_main-var.tmp on /var/tmp type ext3 (rw) []

```

---

### Post by Scorpuk on 2008-06-26
For raid LVM is the way to go.

Your card should allow you to "Auto-Carve" the array into partitions. This will allow you to easily add more partitions to your LVM increasing its size.


I have 3ware Inc 9650SE SATA-II RAID, 12 port, with 12 500GB HDD's attached in RAID-5. The card auto-carves to 2048GB (2TB limit of 32 bit OS) partitions giving me partitions of:

2Tb
2Tb
926.16GB

Resulting in a logical volume of 4.9TB

When installing it is always best to put your OS on a seperate partition from your data.


My setup is:

100GB for boot, root and swap
Remainder mounted in /media/raid5


I learnt this the hard way and originally had:

100MB boot and swap
Remainder as root

OS died and the data died too :(


By doing it the new way I have been able to reinstall the OS and remount the LVM with no data loss at all. :D


Since I wasnt to clued up on volume groups and physical volumes for LVM I used webmin to set it all up. CLI still scares me at times so I prefer GUI's to do things. :-)

---

### Post by batfastad on 2008-06-26
Ah ok

Yeah I realise that after I've added the drives into the RAID 6 array in my 3ware controller, I'll then have to resize the partition to fill the remaining space.

So how will this LVM thing work with my RAID card and RAID 6 array, and allow me to have 1 large partition?

Almost there!! :confused:

EDIT: To clarify... the OS is installed on a separate 120GB drive attached directly to the motherboard SATA sockets. That was always my plan to have the 2 completely separate.

Thanks, B

---

### Post by batfastad on 2008-06-26
@Scorpuk
Yes there is an auto-carve option on my 3ware card.
Is it recommended that I use that?

The card I have is 2x4 multilane sockets, and we have 2x4 bay hot-swap backplane units. Giving us a potential for 8 drives.
At the moment I have 5x500GB drives in a RAID 6 = 1.5TB of space
With another 500GB as a hot-spare.

In a year or so when I want to add 2 more drives... that will push us over the 2TB limit.

So let me get this right...
So if I use that auto-carve, this LVM thing will basically allow me to 'join' these multiple carves into 1 massive partition?

If LVM crashes, or I want to install a different OS on the separate internal drive, will that mangle my data?

---

### Post by justleen on 2008-06-26
> **Scorpuk said:**
> For raid LVM is the way to go.

 CLI still scares me at times so I prefer GUI's to do things. :-)

Tere are some nice other GUI's out there for LVM's..
personally, I find the LVM prompt quite self explanitory.. but then again, that might be just me (we mostly tru64 as OS here.. what gui? :) )

---

### Post by Scorpuk on 2008-06-26
> If LVM crashes, or I want to install a different OS on the separate internal drive, will that mangle my data?


The only way that would happen, I think, is if your card fails!  Very unlikely.


The way it works, haha I think, is that with autocarve it will add the new drives on to the last partition until it hits the set limit and then start a new partition.

ie if I had a 16 port controller and added another 4 x 500GB HDD's my volumes would go something like this:

Volume 1 - 2TB
Volume 2 - 2TB
Volume 3 - 2TB
Volume 4 - 741GB


(My maths may be out ;-))

LVM would then need to be changed to include the new volume. 

Not 100% sure as I went straight for full capacity on my 12 port. lol

EDIT:

If you install new OS on your boot drive all you need to do is reactivate the volume group and then remount it. Exactly what I did when I went from 7.10 to 8.04 (fresh install) - No data loss!

---

### Post by batfastad on 2008-06-26
I've just enabled auto-carving on my controller for 2048GB

So how do I get started with this LVM?

And this will make it so it appears to Linux as 1 massive mountpoint/directory right?
Then I can set-up my individual shares using Samba/Netatalk

Also... this means I don't need to get involved with partitioning with fdisk?
How do I create the file system?

So many questions ;)

Thanks for your help so far!

---

### Post by justleen on 2008-06-26
just install LVM (sudo apt-get install lvm)

at the command line, then type "lvm", this will take you to the lvm prompt.
type help to get a command overview.

very good guide: [http://www.tldp.org/HOWTO/LVM-HOWTO/](http://www.tldp.org/HOWTO/LVM-HOWTO/)
have a look at point 3, and point 11 (and perhaps point 2, for starters...)

an LVM will show multiple disk or partitions as one (or more) partition(s), depening how many volumes you create.

---

### Post by batfastad on 2008-06-26
Ok you guys have persuaded me with this LVM stuff :D
I'm going to give it a go! Seems like it will avoid the pains/dangers of partition resizing in the future.

Tried sudo apt-get install lvm but got:
E: Couldn't find package lvm
I'm on Ubuntu Server 8.04

So opened up Synaptic searched for lvm and found it's now called lvm2, so:
sudo apt-get install lvm2

Then typing lvm at the prompt after that, brings up a prompt saying
lvm>

So far so good.
Until when I type lvcreate to try and make a new LV thing I get the following message:
```
/proc/misc: No entry for device-mapper found
Is device-mapper driver missing from kernel?
Failure to communicate with kernel device-mapper driver.
== THE ABOVE REPEATED AGAIN ==
Incompatible libdevmapper 1.02.20 (2007-06-15)(compat) and kernel driver striped: Required device-mapper target(s) not detected in your kernel
```

I found this topic
[http://ubuntuforums.org/showthread.php?t=689342](http://ubuntuforums.org/showthread.php?t=689342)
And when I follow the instructions and type lsmod | grep dm_* I get exactly the same output.
And I've tried rebooting/powering off and still no luck.

Any ideas?
B

---

### Post by justleen on 2008-06-26
create a device first :)

you cant start with creating a logical volume.. you have to define the disks to use first.

1) pvcreate /dev/hdb1  (replace with correct deivce!!)
2) vgcreate my_volume_group  /dev/hdb1 
reboot
3) vgchange -a y my_volume_group

then, your good to go to create volumes  (the above will create a volume group!)

PS: do check point 11 of that guide ;)

---

### Post by batfastad on 2008-06-26
Ok thanks, will give that a go now... just about to re-boot to create volumes!

Just reading this page under #11 though:
[http://www.tldp.org/HOWTO/LVM-HOWTO/initdisks.html](http://www.tldp.org/HOWTO/LVM-HOWTO/initdisks.html)

The very 1st not recommended bit. That's what I'm about to be doing right?

Why is it not recommended?

I really don't want to go down a route here that can render my RAID array completely unusable/unstable under different operating system scenarios!

Will the logical volume structure be broken if my RAID array gets rebuilt or verified by the controller card, or anything like that?

The way I've understood it so far... my hardware RAID won't care what's going on with the actual drives - it just mirrors or does whatever it needs.

EDIT: Fixed it... I wasn't doing sudo before lvcreate. Seems it should work now!
Now I just have to figure out the options I need to create it as 1 big volume, how to format it as ext3, how to mount it, and how to get it to auto-mount!

Phew :)

---

### Post by Scorpuk on 2008-06-26
:-)


BTW what was the full command you used?

---

### Post by justleen on 2008-06-26
the "not recommend" bit is on a whole disk (/dev/sda) instead of partition (/dev/sda1)

once you have a volume, you can treat is like any other partition. it will show up in fdisk -l..  instead of /dev/sda1 it will be called something like /dev/mapper/my_volumegroup/my_volume

 and your right, RAID does not give a rats *&^ whats on the disks. IT the OS that create partitions / LVM / Data / etc.

so a a RAID check will have no effect. And a rebuild shouldnt have any effect ...

---

### Post by batfastad on 2008-06-26
I've created my vg called raid_group

Then the command I used to create the logical volume was:
```
sudo lvcreate -l 357620 raid_group -n raid_lv1
```
I followed those instructions from the 3rd example: [http://www.tldp.org/HOWTO/LVM-HOWTO/createlv.html](http://www.tldp.org/HOWTO/LVM-HOWTO/createlv.html)

So now I think I have my logical volume created inside my raid_group.
Now what do I do to mount/auto-mount, and to format it as ext3?

So I will be able to increase the size of this LV raid_lv1 up to 2048GB, once I've installed the extra drives in a year or so.
Then create raid_lv2 for the rest of the space, and join them together so they just appear as 1 whole thing?

Does Ubuntu Server not support partitions/devices greater than 2TB?
I still have this feeling it would be easier/safer for me to just create 1 big partition, then resize the partition to fill the space in the array when I add capacity

Thanks for all your help/advice guys - I'm almost there :D

---

### Post by Scorpuk on 2008-06-26
Rebuilds wont have an effect on your data.

The whole point of rebuild is to use the parity data to recreate any lost data due to drive failure.


Or any other destructive means like tripping over your server, like I did. lol


Tripped over it causing IO errors. The raid card spent the next 2 days rebuilding and verifying. For some reason it verified 4 times.


But in the end no loss of data. :D


Praise RAID-5 :KS

---

### Post by batfastad on 2008-06-26
> **justleen said:**
> the "not recommend" bit is on a whole disk (/dev/sda) instead of partition (/dev/sda1)

Ah... that's exactly what I just did.
My raid device showed up to the system as /dev/sda, not /dev/sda1

---

### Post by justleen on 2008-06-26
with the auto scraping on?

you should have more then one partition..

though it doest matter, really.. you just a assing a whole disk to a LVM, instead of a partition...
not common practice thats all (and not recommend, but he, a lot of thing are not recommend ;)

---

### Post by batfastad on 2008-06-26
> **justleen said:**
> with the auto scraping on?
you should have more then one partition..

Yeah the auto-carving is set to 2048GB on the controller
I only have a capacity of 1.5TB at the moment because I'm using RAID 6.

I've not created any partitions on the drive yet - do I need to create partitions before I create the group?
I thought this LVM thing would avoid the partitions over 1TB issues?

I've been messing around with this for a few minutes, creating groups, volumes, deleting volumes etc.
But I can't work out how to mount the volume once it's created

Cheers, B :D

---

### Post by Scorpuk on 2008-06-26
my fstab is as follows:

```
/dev/VG-Data/LV-Data     /media/raid5       reiserfs       suid,dev,exec  0  0
```

VG-Data is the Volume Group name
LV-Data is the Logical Volume Name

resierfs is the file system as I followed an old mythtv guide and left my brain at work (cant change it now as over 1.5TB data on the drive)

---

### Post by Scorpuk on 2008-06-26
Hmmm another question for you:


How exactly did you setup the drives in the RAID controller?

---

### Post by batfastad on 2008-06-26
I used the 3Ware BIOS Manager interface
Selected the disks I wanted to use (all but 1) then chose create unit.
I told it to create a RAID 6 unit, then it whirred away for an hour or so and said it was deleting anything that was currently on those 5 drives.
Then there it was in Ubuntu... /dev/sda

Once I got the 3DM2 service up and running, I selected the final 6th drive as a hot-spare using the 3DM2 web interface.

Why... is that a problem?

For the record, I've decided not to use LVM for the moment.
It's just too much of a step right now. I need to get this machine up and serving files by the start of next week. And I'm so new to Linux as it is, I would rather wait to make that next step.
So I used fdisk to create one big partition, now called /dev/sda1, and formatted that as ext3 using mkfs

LVM definitely sounds like the way to go though once I start getting to larger capacities and need to add further drives. This will definitely be something I'll be looking to do in 4-6 months time.

Thanks for all the help so far :D
B

---

### Post by Scorpuk on 2008-06-26
I think I have it now, lol.


You have auto carving at 2Tb and have a capacity of 1.4TB


ergo you have sda showing on the system.


IF you have over 2TB you would have had sda and sdb showing on the system.


On my system since I have 5TB, approx, available I have sda, sdb, sdc and sdd with sda being the 100GB boot root and swap.


Since I used webmin and kind of fluffed my way through it I'm not sure how I partitioned those into sdb1, sdc1 and sdd1. But I did  and then grouped them together for the LVM.

I think it was:
1. create volume group [VG-Data]
2. assign physical volumes to the group (sdb, sdc and sdd?)
3. create logical volumes group [LV-Data] (possibly formatted and mounted here)

If I get time at work tomorrow / sat I'll create a vm machine with 5 drives and have a bash at the cli way of things. :D

vm has been a life saver in trialing stuff out. :D

To future proof your system LVM is deff the way forward.


Only down side to your spec is the fact you have gone for 500GB drives when 1TB drives are falling in price...


Think of it this way, my only way to expand from 5Tb is to add in a second raid card or switch out ALL 12 500GB drives for higher capacity ones. :|

Anywho looking forward to getting a rackmount server case, once I check insurance for putting it in the garage. :-)

---

### Post by batfastad on 2008-06-26
I tried turning the auto-carving down to 1024GB, with by 1.4TB total but still the auto-carving didn't seem to kick in.
Restarted and powered off/on and nothing.

I think maybe I have to tell the card to rebuild or something.

Once I created the partition in fdisk though (don't know why cfdisk didn't work), then I had /dev/sda and /dev/sda1. So I'm using /dev/sda1 right now and it works great.

Either way, for now I'm up and running but I'll be coming back to this post when I decide to take the plunge with LVM. Definitely seems like the way forward when we start getting to big capacities.

At the moment I've designed our NAS to be pretty future-proof - 1.4TB seems like loads to us at the moment (no doubt in a year that will change though).

I'll be experimenting with LVM over the next couple of months to try and get it figured out more

Thanks for all your help guys! :D
B

---

