---
title: "fdisk does not create usuuable partitions"
date: 2008-06-11
forum: General Help
---

### Post by RaygionsSumta on 2008-06-11
I am seeing some of the darnedest behavior on my theoretically fresh (as of last night) Hardy Heron installation.  Ultimately, my three 400GB SATA drives are not being recognized by the system outside of the context of fdisk.  That is to say, that I can fdisk the drives and create a partition on each, but am unable to perform any operations on that partition. In fact, the fdisk-ing is not creating a /dev/sda1.

I have gone so far (perhaps too far) as to try and create an sda1 with
 sudo mknod /dev/sda1 b 8 1

While it does make the entry in the dev directory, it does not seem to signify. This problem has survived two complete reinstalls.  Any suggestions?

Joe

> 
joe@ariadne:~$ sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006e470

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48641   390708801   83  Linux

[other drives info deleted]

joe@ariadne:~$ sudo mkfs.ext3 /dev/sda1
mke2fs 1.40.8 (13-Mar-2008)
Could not stat /dev/sda1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

---

### Post by logos34 on 2008-06-11
What about gparted?  Delete the partition and create a new one.

If gparted doesn't show anything, I'll give you the dd command to nuke the whole drive.  Then start over.

---

### Post by new_at_linux on 2008-06-11
> **logos34 said:**
> What about gparted?  Delete the partition and create a new one.

If gparted doesn't show anything, I'll give you the dd command to nuke the whole drive.  Then start over.

Could the nuke command fix my problem? [http://ubuntuforums.org/showthread.php?t=824147](http://ubuntuforums.org/showthread.php?t=824147)

---

### Post by logos34 on 2008-06-11
> **new_at_linux said:**
> Could the nuke command fix my problem? [http://ubuntuforums.org/showthread.php?t=824147](http://ubuntuforums.org/showthread.php?t=824147)

simonsambler has replied to your thread.  What does fdisk show?

---

### Post by RaygionsSumta on 2008-06-11
> **logos34 said:**
> What about gparted?  Delete the partition and create a new one.

If gparted doesn't show anything, I'll give you the dd command to nuke the whole drive.  Then start over.

I removed then recreated the partition with gparted.  Then I tried to format it to the error below.  

This is my nth wipe and reinstall as I try to get a software raid to configure.  It appears that raid, and perhaps other, information is being carried across the installs, despite my deletion of the partitions on the SATA drives, and my Erasing of the data on the boot drive when I reinstall.  I have not touched mdadm for the last two reinstalls, as I have been unable to do anything to the drives, save fdisk them.

-------------------------------------------
GParted 0.3.5

Libparted 1.7.1

Format /dev/sda1 as ext3  00:00    ( ERROR )
     	
calibrate /dev/sda1  00:00    ( SUCCES )
     	
path: /dev/sda1
start: 63
end: 781417664
size: 781417602 (372.61 GiB)
set partitiontype on /dev/sda1  00:00    ( SUCCES )
     	
new partitiontype: ext3
create new ext3 filesystem  00:00    ( ERROR )
     	
mkfs.ext3 /dev/sda1
     	
mke2fs 1.40.8 (13-Mar-2008)
Could not stat /dev/sda1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

---

### Post by logos34 on 2008-06-11
oh, so raid is involved.  I don't have much experience with that, so I'll have to defer to someone else.

Raid0,1,5?

---

### Post by cdtech on 2008-06-11
Have you tried the makedev command within the /dev directory? You may not have the sd's listed.

Just a thought.

Never mind, my bad, just seen the raid......

---

### Post by RaygionsSumta on 2008-06-11
> **logos34 said:**
> oh, so raid is involved.  I don't have much experience with that, so I'll have to defer to someone else.

Raid0,1,5?

Raid 5.  But at this point, I have deleted the partitions on the drives that will be used for raid as well as repartitioned and reformatted the boot drive.  This is a brand-spanking-new installation.  In theory, there should be no trace of raid.   I should be able to partition one of the 400GB SATAs, and then reformat it.  Or so I would like to believe.

---

### Post by RaygionsSumta on 2008-06-11
> **logos34 said:**
> What about gparted?  Delete the partition and create a new one.

If gparted doesn't show anything, I'll give you the dd command to nuke the whole drive.  Then start over.

Running gparted from a term gives me "No such file or directory during read on /dev/md0"  when there is supposedly no software raid running.  Aside from /etc/mdadm/mdadm.conf and /dev/md0, I wonder where I might find little files that make linux think that my drives are part of an array.  so much minutae.  Thats what makes this fun and frustrating!

---

### Post by logos34 on 2008-06-11
> **RaygionsSumta said:**
> Running gparted from a term gives me "No such file or directory during read on /dev/md0"  when there is supposedly no software raid running.  Aside from /etc/mdadm/mdadm.conf and /dev/md0, I wonder where I might find little files that make linux think that my drives are part of an array.  so much minutae.  Thats what makes this fun and frustrating!

Did you disable raid in the Bios?

---

### Post by RaygionsSumta on 2008-06-12
> **logos34 said:**
> Did you disable raid in the Bios?

Blink.  
Blink.  Blink. 

My choices are IDE, RAID and AHCI.  Its set on AHCI(Advanced Host Controller Interface).  

I will investigate [ [http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface#Common_problems_switching_to_AHCI_under_Linux](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface#Common_problems_switching_to_AHCI_under_Linux) ] tommorow after I get some sleep.

Thanks for the thought

Joe

P.S. Gotta love that chromosome 2!

---

