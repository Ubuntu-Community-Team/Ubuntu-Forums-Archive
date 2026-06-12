---
title: "Problems with raid-1 on 7.10"
date: 2007-11-02
forum: General Help
---

### Post by boureyborin on 2007-11-02
Hi.  I'm having problem configuring raid-1 on ubuntu 7.10.

I have 3 sata drives: one 160GB and two 500GB.  I'd like to setup the two 500GB drives partitioned as two raid-1 devices.   The drives show up as sda, sdb, and sdc, respectively.

During install, I partition the 160GB as / (root) and swap.  I don't partition the 500s.
Installation is successful.

Then I use cfdisk to partition sdb and sdc.  I make identical partition sizes (two partitions total) on both drives.  The partitions are of type linux raid autodetect.

This leaves me with new device files sdb1, sdb2, sdc1, sdc2.

I then use mdadm to create the raid devices:

mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
mdadm --create /dev/md1 --level=1 --raid-devices=2 /dev/sdb2 /dev/sdc2

This appears to work.  Looking at /proc/mdstat I see both raid devices active and syncing.

Then I reboot and things go bad.

The sdb1, sdb2, sdc1, and sdc2 files are gone.  The sdb and sdc files are still there.  cfdisk still reports both partitions are on both drives.  However, /proc/mdstat now only shows md0.  And /dev/md1 is gone.

Also, during boot (sometimes) the system stalls for 2-3 minutes with lots of disk activity.  Running in failsafe mode shows the following error messages printed over and over...

md: _import_device returned -22
md: invalid raid superblock magic on sda2
md: sda2 has invalid sb, not importing!

sda2 is my swap partition.  Why is the system complaining about raid superblocks in my swap?

Anybody know what I'm doing wrong here?

---

### Post by fjgaude on 2007-11-02
Some things to try:

```
sudo mdadm -D /dev/md[n]
```

and

```
sudo mdadm --assemble --scan --verbose
```

Let's see what such gives?

---

### Post by boureyborin on 2007-11-02
> mdadm -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu Nov  1 08:29:45 2007
     Raid Level : raid1
     Array Size : 488386496 (465.76 GiB 500.11 GB)
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Nov  2 00:40:18 2007
          State : clean, resyncing
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

 Rebuild Status : 47% complete

           UUID : b8f50ee2:5c4e5066:0a0d2d7c:22bc74a9 (local to host linux-dt-1)
         Events : 0.19

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc


> mdadm -D /dev/md1
mdadm: md device /dev/md1 does not appear to be active.


> mdadm --assemble --scan --verbose
mdadm: looking for devices for further assembly
mdadm: no recogniseable superblock on /dev/disk/by-id/md-uuid-b8f50ee2:5c4e5066:0a0d2d7c:22bc74a9
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: cannot open device /dev/sda2: Device or resource busy
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: No arrays found in config file or automatically


The partition sizes for the 500GB drives were setup as 16GB (md0) and 480+GB (md1).  But md1 is missing and md0 seems to be the big partitions (or using the entire drives).

---

### Post by fjgaude on 2007-11-02
What you observe seems to be correct... the whole disks because they show as sdb and sbc, not sdb2 or sdc2.

Don't know what to say except to start over and be very careful for what you do. Sorry about that. If you start over you will have to release the partitions from the two drives by using 

sudo mdadm -S /dev/sd[nn]

to deactivate the arrays.

---

### Post by boureyborin on 2007-11-02
Ok, I'll try that.

Does it matter when I make a filesystem on the paritions?  Does it need to be before or after I make the array?  Or it doesn't matter?

Any idea why I get the "invalid SB" messages for sda2?

---

### Post by fjgaude on 2007-11-02
Make the filesystem after you create the array, yes. Can't say things haven't worked out so far.

Here's the way I'd do it from the start:

```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
sudo mkfs -t ext3 /dev/md0
sudo cat /proc/mdsta
```

After the cat shows the drives are in sync, check to see we truly have a good array:

```
sudo mdadem -R /dev/md0
```

Then I'd mount the array:

```
sudo mount /dev/md0 /media/mountpoint
```

Then I'd copy files to the array. Let us know how things go. Luck to you. <smile>

I don't know why you need a swap partition, you don't. That is likely on your sda1, eh?

---

### Post by boureyborin on 2007-11-02
Hmm.  So when the array is stopped with mdadm -S /dev/md0 the individual paritions (sdb1 and sdc1) are supposed to reappear in the /dev directory?  This isn't happening.  mdadm thinks the arrays are stopped (the md0 file is no longer present), but the individual partitions devices never return.  So I can't try to restart the arrays.  I've reinstalled ubuntu 3 times now and the results are always the same: I create the array, the array seems fine, I reboot, then the arrays devices are corrupted.

---

### Post by fjgaude on 2007-11-02
Do you have data on the drives? Are you installing the filesystem after you make the array?

I'm at a loss to understand what might be happening.

---

### Post by boureyborin on 2007-11-03
I am installing the filesystem.  I haven't had much more luck.  Maybe you can answer some basic questions for me:

1. Once the arrays are created with mdadm, are they permanent?  I've been assuming that the mdadm commands are a one-time thing and after that the system "knows" about the raid array.  Do I need to put the mdadm commands in an init script somewhere?

2. For your raid, do you use mdadm.conf?  The initial howto stuff I read seems to indicate that the mdadm command themselves were sufficient.  Is the mdadm.conf file required?

3. Where is the mdadm.conf file supposed to be located?  I see one in /etc/mdadm/mdadm.conf after install.  But I've read some online sites that refer to /etc/mdadm.conf instead.


Thanks for the help.

---

### Post by fjgaude on 2007-11-03
> **boureyborin said:**
> I am installing the filesystem.  I haven't had much more luck.  Maybe you can answer some basic questions for me:

1. Once the arrays are created with mdadm, are they permanent?  I've been assuming that the mdadm commands are a one-time thing and after that the system "knows" about the raid array.  Do I need to put the mdadm commands in an init script somewhere?

2. For your raid, do you use mdadm.conf?  The initial howto stuff I read seems to indicate that the mdadm command themselves were sufficient.  Is the mdadm.conf file required?

3. Where is the mdadm.conf file supposed to be located?  I see one in /etc/mdadm/mdadm.conf after install.  But I've read some online sites that refer to /etc/mdadm.conf instead.

Thanks for the help.

1. They ae permanent until you release a device, drive using mdadm /dev/md[n] -r /dev/sd[nn]

2. mdadm.conf is used only if a --scan is not able to locate the devices to assemble. You as a user don't use the .conf file. As far as I know the file is not needed, but I'm no expert.

3. The file is now in /etc/mdadm/. In older systems it is in /etc/.

I've been thinking, perhaps an issue with what you have been doing is the naming of the arrays when you have more than one partition on a device. Notice near the end of man mdadm how the standard names are to be.

Keep at it and let us know how you are doing.

---

### Post by boureyborin on 2007-11-03
Could you be more specific?  You mean the names of the arrays?  I'm calling them md0 and md1.  What are the standard names?

---

### Post by fjgaude on 2007-11-03
> **boureyborin said:**
> Could you be more specific?  You mean the names of the arrays?  I'm calling them md0 and md1.  What are the standard names?

Look near the bottom of the man pages for mdadm. There it shows naming standards for partitions beyond using sda1, but sda2.

```
man mdadm
```

I've neve done an array that uses other than one partition.

---

### Post by boureyborin on 2007-11-04
Well, I think I got it working - maybe it was just stupid mistakes on my part.  Here's what I did:

1) Partition both sdb and sdc with 2 identical partitions
2) Use mdadm to create two raid-1 devices (md0=sdb1+sdc1, md1=sdb2+sdc2)
3) Wait for both raid devices to finish sync'ing
4) mkfs on both /dev/md0 and /dev/md1
5) Add the appropriate ARRAY and DEVICE lines to /etc/mdadm/mdadm.conf
6) mount both /dev/md0 and /dev/md1
7) Add the appropriate lines to /etc/fstab
8) Reboot

Now the raid devices survive past the reboot and appear to be working.

Before, I assumed I could reboot after step 2.  I'm pretty sure I also tried rebooting after step 3.  But this never worked - the machine would come back up with md1 missing and md0 composed of the entire disks (not just the first partitions).

I'm still confused (and a little nervous) about the above list - it all seems very fragile.  I'm not sure which steps are required and in what order.  For instance, individual drives (sdb, sdc, etc) are allowed to just "exist" in the system with no partitions, filesystem, and unmounted.  I had assumed after creating the array with mdadm, the md0 device would just "exist" as if it was a HW drive.  And later I could partition it, create a filesystem, mount it etc.

Anybody know which step(s) above are the magic steps?  I'm not sure step 5 is needed  - I've heard the config file is optional and I've heard it is required.  I set it up just to cover my bases.

Anyway, thanks for all the help fjgaude!

---

### Post by fjgaude on 2007-11-04
1) Partition both sdb and sdc with 2 identical partitions
2) Use mdadm to create two raid-1 devices (md0=sdb1+sdc1, md1=sdb2+sdc2)
3) Wait for both raid devices to finish sync'ing
4) mkfs on both /dev/md0 and /dev/md1
5) Add the appropriate ARRAY and DEVICE lines to /etc/mdadm/mdadm.conf
6) mount both /dev/md0 and /dev/md1
7) Add the appropriate lines to /etc/fstab
8) Reboot

Seems like it works, eh? By what you said you were jumping the gun at first by not letting things finish before rebooting. After making an array I don't think you can later partition it. I've never have even tried. An md0 or md1 is an array, not a device but a Multiple Device, MD.

Once created the OS knows it for sure. Please study the man page to get a better understanding as to how to change things as time goes on, if needed.

Put some data on it and see if you can reboot correctly and have it show when at the desktop.

For the last time, what are you going to do the the swap array?

I tell you, most folks need a Linux technician to get as fast as you have. Congrats.

---

### Post by boureyborin on 2007-11-04
"For the last time, what are you going to do the the swap array?"

Not sure what your question means (seems like a typo somewhere in there).  Do you mean swap partition?  Or raid array?

The arrays are for /home on the ubuntu system (md0) and for "samba network storage" (md1) to provide a common location for digtal photos, documents, mp3, etc. from all the other desktops/laptops in the house.

So I have two 500gb drives, each with two partitions (first partition on each is for /home, second partition on each is for NAS).  The OS is on a 3rd drive (partitioned with 1gb of swap - I know, many people say you don't need swap but I couldn't help myself :))

I also have a 4th drive (another 500gb) and a hotplug cage.  The idea is I'll periodically plug in the 4th drive and use "dd" to clone the raid arrays to the "removable" drive.  I'll store that drive offsite.  I tried this today and it worked great.

Now it's on to configuring samba...

---

### Post by fjgaude on 2007-11-04
Since I don't think you have an OS on the array, the question of why do you have a swap partition on the two array drives?

I understand the OS is on a single drive with its own swap partition. Fine...

Good luck with samba; it's a snap with Ubuntu.

---

### Post by boureyborin on 2007-11-05
I don't have swap on the array drives.  Only the os drive.

---

### Post by fjgaude on 2007-11-05
Very good, two partitions on the raid array. Bravo!

Enjoy your new found knowledge.

---

