---
title: "Preparing mount points"
date: 2006-10-30
forum: General Help
---

### Post by band-aid on 2006-10-30
Whenever I try to proceed past the Prepare mount points section of the installer (5 of 6) it says: "no root file system" But I do have a root file system. My partitions are as such.

sda1 == my windows install
hda1 == my other drive for random stuff
hdb1 == 297 gig partition for more random stuff
hdb2 == /
hdb3 == a 1kb partition I made on accident :D
hdb5 == a 6 gig linux swap partition.

I have it set up in the little window like this.

mount point        size        partition        reformat?
/                   15 gb      hdb2                 yes
swap                 6gb       hdb5                 yes

I click next and it says I have no root file system. I would prefer not to stuff my windows partitions so I am treading lightly. Thanks in advance.

---

### Post by CatKiller on 2006-10-30
hdb5 is a logical drive in an extended partition. If hdb2 is that extended partition, then you can't use it to install Ubuntu in - an extended partition is just a box for the logical drives.

Oh, and 6 Gig is a bit big for swap - around twice your RAM or 2 Gigs, whichever is the smaller, will do you fine.

---

### Post by band-aid on 2006-10-31
so, what do I need to do to fix this without destroying all the data on the disk?

---

### Post by bsussman on 2006-10-31
first post a detailed description of the partition structure, so we can verify what is what.  This should include filesystem type, if any and what is nested within what.  Catkiller is almost certainly correct and it would nice to be as careful in answering as you are being in preserving your current data :)

Also - state what you want for partitions to hold ubuntu - of course / and swap.  What else?  a separate home?  usr?  boot?

---

### Post by band-aid on 2006-10-31
ok heres all I can get out of the installer as far as partition information.



/dev/hda1 is filesystem ntfs 64.53 GB - this drive is 1 partition and stores windows junk, I don't want it dead or erased :D .

/dev/hdb1 is filesystem ntfs 277.16 GB 

/dev/hdb2 is filesystem ext3 15.12 GB has 2.49 GB of a Debian install in it. It is flagged as boot, this is where I would like my root directory to go.

/dev/hdb3 is filesystem extended is 5.80 GB is flagged as lba.
/dev/hdb5 is filesystem linux-swap is 5.80 GB. This is what I want to use as swap space.

/dev/sda1 is filesystem ntfs is 69.23 GB. This is my windows hard drive, I REALLY don't want it dead or erased. :D

I think that pretty much covers it. If ya need anything else I'll do my best to figure it out.

---

### Post by bsussman on 2006-11-01
> **band-aid said:**
> ok heres all I can get out of the installer as far as partition information.



/dev/hda1 is filesystem ntfs 64.53 GB - this drive is 1 partition and stores windows junk, I don't want it dead or erased :D .

/dev/hdb1 is filesystem ntfs 277.16 GB 

/dev/hdb2 is filesystem ext3 15.12 GB has 2.49 GB of a Debian install in it. It is flagged as boot, this is where I would like my root directory to go.

/dev/hdb3 is filesystem extended is 5.80 GB is flagged as lba.
/dev/hdb5 is filesystem linux-swap is 5.80 GB. This is what I want to use as swap space.

/dev/sda1 is filesystem ntfs is 69.23 GB. This is my windows hard drive, I REALLY don't want it dead or erased. :D

I think that pretty much covers it. If ya need anything else I'll do my best to figure it out.

Reconfirm you want to do this during an install of ubuntu?

Use manual partitioning/assignment

Much of the following will be right when it displays the choices.


/dev/hda1 
 
and

/dev/hdb1 should be configured to mount on /media/...

/dev/hdb2 should be mounted on / - I assume you want to blow this away and reformat as you install.

/dev/hdb3 I think you should increase this by the amount you shrink your swap and mount as /home

/dev/hdb5 iis too big - 2gig or 2xmemory , whichever is smaller, is the max although wasting more will not cause problems.

/dev/sda1 - should should be configured to mount on /media/...

MAKE DARN SURE THE REFORMAT CHECKBOX IS OFF FOR THE PARTITIONS YOU DO NOT WANT ERASED.  This is your biggest hazard.

You can do the hdb3/5 adjustment easily - gparted is available during install and the current content seems to be expendable.  You want to do that?

Have no fear of screwing up unless you do not read carefully.  It will tell you what it is going to do before changing anything.


Does this make sense?  This is a fairly typical setup.

There is one point I need confirmation on - I do not know if the install will correctly find the win os on sda1.  I am used to all disks being the same type (sata OR IDE OR scsi).  If it does not, you would need to manually add it which is going to probably make you nervous (It would me) though many have done it.  This is your second biggest hazard.

I am trying to impart some knowledge along with the correct steps.  I figure you should know why as well as what to do.

---

### Post by band-aid on 2006-11-01
chalk up another problem solved by the ubuntu community. Thanks for the help. :D

---

### Post by antharr on 2006-11-11
I am having the same problem but my swap is a reasonable size @ 500MB.
Here is my setup.

I have 2 Hard drives. My slave is 160 gigs and nothing more than for file storage. My master is an 80 gig with WinXP installed on the first 60 gigs. I have another 19 gig primary partition where I would like to install Ubuntu and a 500MB partition for a swap. At the prepare mount point window, here is how things are set up and I still get the "No root file system message". 

/media/hda1    55 GB Partition 1 Disc IDE/ATA 1 (Primary) [hda1]
/              19 GB Partition 2 Disc IDE/ATA 1 (Primary) [hda2]
swap           502MB Partition 3 Disc IDE/ATA 1 (Primary) [hda3]
/media/hdb2    149GB Partition 2 Disc IDE/ATA 1 (Primary) [hdb2]

Does anyone have a clue what may be wrong here? Thanks

---

### Post by antharr on 2006-11-11
Nevermind.Just fixed it. I had to delete the current ext2 partition and then create a new ext3. Worked perfectly.

---

### Post by Palypup on 2006-11-24
After numerous disasterous installs of assorted linux distros,
I have discovered that by disconnecting essential drives by pulling
the data cable or power cable (doesn't hurt to do both), I can muck
about to my heart's content and not worry about loosing an OS or data
that are not available during format and install of new OS. In other
words, isolate the space you want to play with from the stuff you want
to keep by removing power or data transfer.

---

