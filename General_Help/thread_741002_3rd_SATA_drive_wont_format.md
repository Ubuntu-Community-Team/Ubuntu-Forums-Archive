---
title: "3rd SATA drive wont format"
date: 2008-03-31
forum: General Help
---

### Post by Rizla on 2008-03-31
I finished installing a Gusty 64 bit server and am in the processes of trying to setup raid 5.  In order to do so I had to format my (3) 750GB disks.  The first two went well.  The last one didnt..

When I try and run sudo fdisk /dev/sdc i get the following error:

Unable to read /dev/sdc

When i try and run sudo fsck -f -v /dev/sdc I get this:

Attempt to read block from filesystem resulted in short read while trying to open /dev/sdc


Is the drive bad?  I just bought these brand new last week.. I'd hate for 1 out of 3 to be bad.  I dont want to deal with RMA and all that crap.  Is there anything else i can try from the OS side.  I'm going to check bios to make sure its still showing up.

Any help would be greatly appreciated.  Thanks.

---

### Post by dannyboy79 on 2008-03-31
so right now it's not formated? what does this return?

sudo fdisk -l

it should return all your hard disks and if they have any partitions. like this:

Disk /dev/hdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       36483   293049666    b  W95 FAT32

Disk /dev/hdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1          13      104391   83  Linux
/dev/hdc2              14        1281    10185210   83  Linux
/dev/hdc3            1282        1472     1534207+  82  Linux swap / Solaris
/dev/hdc4            1473        2434     7727265   83  Linux

Disk /dev/hdd: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       36483   293049666   83  Linux

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48641   390708801   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Your drive could very well be bad, it does happen. What does Gnome Partition Editor show? Or do you not have a window manager installed?

---

### Post by Rizla on 2008-03-31
> **dannyboy79 said:**
> so right now it's not formated? what does this return?

sudo fdisk -l

it should return all your hard disks and if they have any partitions. like this:

Disk /dev/hdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       36483   293049666    b  W95 FAT32

Disk /dev/hdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1          13      104391   83  Linux
/dev/hdc2              14        1281    10185210   83  Linux
/dev/hdc3            1282        1472     1534207+  82  Linux swap / Solaris
/dev/hdc4            1473        2434     7727265   83  Linux

Disk /dev/hdd: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       36483   293049666   83  Linux

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48641   390708801   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Your drive could very well be bad, it does happen. What does Gnome Partition Editor show? Or do you not have a window manager installed?

it was formatted before.  I created the partition, then ran the mksf command, it returned an error at the end.

I rebooted the server (by the way, i'm SSH from work so i can physically inspect the drives/wiring) and now when i do a fdisk -l i'm only seeing the initial 2 750GB drives and my other 500GB..

I think its a hardware problem since linux doesnt even see it anymore. Any other options for remote troubleshooting?

---

### Post by dannyboy79 on 2008-03-31
not for remote troubleshooting, sorry. You'd have to make sure cabling is good to go.

---

### Post by Rizla on 2008-03-31
> **dannyboy79 said:**
> not for remote troubleshooting, sorry. You'd have to make sure cabling is good to go.

Figured thats the case.  I'm hoping its a faulty cable and not the drive.. or a bad sata port.

Have you set up raid before?  Do you have to create the filesystem before your create the raid set?

I was following this tut:
[http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)

I skipped the first part because i cant use gparted because I dont have gnome.  So i just used fdisk to create the partitions on each drive.  I made a primary linux partition using the whole disk.  Afterwards I formated with the ext3 file system.

The part that hung me up and wasnt sure what the equivalent was in fdisk was how to set the raid flag.

After doing some searches, i think I did it correctly by doing and fdisk /dev/sda (for each drive)

then typing "t"
then typing "fd" which is the hex code for Linux Raid autodetect (im assuming thats what the raid flag was)

I noticed though when i typed the "p" command the ID was changed to 'fd' from '83'  The filesystem should still be ext3 right?

I dont know why i just explained all this beacuse this thread isnt about the raid setup, but maybe you know..

---

### Post by dannyboy79 on 2008-03-31
i'm sorry, I've never dealt with RAID setup. good luck though.

---

### Post by fjgaude on 2008-03-31
You create the filesystem after you create the raid array.

Usually the drives that go into an array have some filesystem on them but it makes no difference. The filesystem that the array will use is put on after the creation, the --create command of mdadm.

---

### Post by Rizla on 2008-04-01
Well, it turns out the drive crapped the bed.  I replaced it with a new 750GB, partioned it with a primary partition, then formated it with the ext3 filesystem, lastly added the hex flag 'fd' for "linux raid auto detect".  I then created the raidset with mdadm.

Currently is setting it up.  So far we're coming up on  4 hours (~20 mins left)  total time to create a 1.5TB Raid5 set.  All thats left to do is edit my fstab and mount.  I hope i'm good to go after that..  Wish me luck, i've had a bit of s truggle with gusty 64 bit server so far..

---

### Post by dannyboy79 on 2008-04-01
well as the previous poster, says, you're suppose to create the filesystem after you create your raid array so hopefully your way will work also. I can't speak for it but wanted to make sure you read the post number 7

---

