---
title: "Setting up software raid/having hard fail issues"
date: 2007-12-26
forum: General Help
---

### Post by John Lentz on 2007-12-26
Hi,

I'm trying to get a raid 5 system setup and tested.  I have my OS (Gutsy Gibbon) on a single harddrive and then I have 3 harddrives I'm trying to get set up in raid 5.  I have them up and running, but now I'm trying to see what happens for different failure modes.  I've run through the raid howto and I can use software to fail a drive, and get the array up and running again.  However, the problem I'm having is that when I unplug the sata cable (with power off) and turn on the machine, I start getting error messages and it won't bring up the raid array.  According to the howto, it should handle this just fine.  When I turn power on I get the following message: fsck.ext3: Invalid argument while trying to open /dev/md0 and then /dev/md0:  The superblock could not be read or does not describe a correct ext2 filesystem.  If the device is valid and it really contains an ext2 filesystem ....

I built it with ext3, so I'm not sure what to do.  

If I cntr-alt-del and let it continue booting, I end up at the desktop (since I'm booting from another drive)

If I try to mount the raid (mount -t ext3 /dev/md0 /nas), I get mount: wrong fs type, bad option, bad superblock on /dev/md0, ....

Could someone please explain what I've done wrong?

Thank you,

John

---

### Post by tgilber1 on 2007-12-26
Need a little more info than what you have give such as mdadm.conf, fstab, "tune2fs -l <md<0-9>", and "sudo fdisk -l" to help out.

---

### Post by John Lentz on 2007-12-26
> **tgilber1 said:**
> Need a little more info than what you have give such as mdadm.conf, fstab, "tune2fs -l <md<0-9>", and "sudo fdisk -l" to help out.

With it plugged back in, it works/boots fine and here is the info:
mdadm.conf:  
DEVICE partitions
CREATE owner=root group=disk mode=0660 auto=yes
HOMEHOST <system>
MAILADDR root
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=24ebe3a8:79d3d3d3:de0e0226:248708a6 spares=1

?? strange about the spares, since I only have 3 devices in the normal raid 5 array

fstab:
<stuff>
/dev/md0   /nas  ext3  defaults  1  1

tune2fs -l /dev/md0:
Filesystem volume name: <none>
Last mounted on:  <not available>
UUID: numbers here
filesystem magic number: 0xef53
filesystem revision #: 1 (dynamic)
filesystem features:  has_journal resize_inode dir_index filetype needs_recovery sparse_super large_file
filesystem flags: signed directory hash
default mount options: (none)
filesystem state: clean
errors behavior: continue
OS: linux
inode count: 244203520
block count: 488379968
reserved block count: 24418998
free blocks: 479138099
free inodes: 244202226
first block: 0
block size: 4096
fragment size 4096
reseved gdt blocks: 907
....
mount count 4
max mount count 37
..
first inode: 11
inode size: 128
journal inode: 8
....

sudo fdisk -l
disk /dev/sda: 100.0 gb
/dev/sda1   *     1     11661   93666951  83 Linux
/dev/sda2          11662   12161   4016250  5  Extended
/dev/sda5        11662   12161  4016218+  82 Linux swap/solaris

disk /dev/sdb 1000.2 gb

/dev/sdb1   1   121601  976760001  83 Linux

same for /dev/sdc1 and /dev/sdd

Disk /dev/md0: 2000.4 gb
2 heads ...
units-cylinders of 8 * 512 ....
disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table



There is the output you mentioned:  The spare disk issue and that last statement about valid partition table is strange.  The raid5 works ok when I have all disk plugged in.  Thanks so much for any help.

John

---

### Post by fjgaude on 2007-12-26
> fstab:
<stuff>
/dev/md0 /nas ext3 defaults 1 1

That is not right, from my knowledge; use:

```
/dev/md0 /nas ext3 defautls 0 2
```

I can't say if this will help. Pray tell, what does the -D command of mdadm show:

```
sudo mdadm -D /dev/md0
```

---

### Post by tgilber1 on 2007-12-26
> **John Lentz said:**
> With it plugged back in, it works/boots fine and here is the info:


sudo fdisk -l
disk /dev/sda: 100.0 gb
/dev/sda1   *     1     11661   93666951  83 Linux
/dev/sda2          11662   12161   4016250  5  Extended
/dev/sda5        11662   12161  4016218+  82 Linux swap/solaris

disk /dev/sdb 1000.2 gb

/dev/sdb1   1   121601  976760001  83 Linux

same for /dev/sdc1 and /dev/sdd

Disk /dev/md0: 2000.4 gb
2 heads ...
units-cylinders of 8 * 512 ....
disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table



There is the output you mentioned:  The spare disk issue and that last statement about valid partition table is strange.  The raid5 works ok when I have all disk plugged in.  Thanks so much for any help.

John

I stand corrected.  I was wrong in my previous post.  I based my post upon raid 1 setup.  Please refer to URL link and post below

Reference:  [http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)

---

### Post by psusi on 2007-12-26
Do NOT follow the above post's advice.  It appears that you have linux installed and booting on sda, and only sdb, sdc, and sdd are involved in the raid, so you do not want to wipe out sda.  

Your partition table on the 3 raid disks lists the partition type as Linux.  This technically should be Linux Raid Autodetect, though it doesn't matter that much.  You can use fdisk to change this with the t command and save it.  

Your problem is a known issue.  The system will not activate a raid set in degraded mode by default, because the remaining disk just might not have been detected yet.  You will need to manually activate the array with sudo mdadm -A /dev/md0.

---

### Post by John Lentz on 2007-12-27
> **psusi said:**
> Do NOT follow the above post's advice.  It appears that you have linux installed and booting on sda, and only sdb, sdc, and sdd are involved in the raid, so you do not want to wipe out sda.  

Your partition table on the 3 raid disks lists the partition type as Linux.  This technically should be Linux Raid Autodetect, though it doesn't matter that much.  You can use fdisk to change this with the t command and save it.  

Your problem is a known issue.  The system will not activate a raid set in degraded mode by default, because the remaining disk just might not have been detected yet.  You will need to manually activate the array with sudo mdadm -A /dev/md0.

Thanks for the reply.  I tried sudo mdadm -A /dev/md0, and it came back with 'no devices found for /dev/md0'.  Is there something else I should have done?  Also, I plugged in the 3rd hard drive to get the array working again and took a look at fdisk.  I'm not sure what to do with the t command to switch it to autodetect.  However, using the p option, it said I didn't have any partitions defined.  I can still save data to it though - not sure why.

Thanks again for any help.

John

---

### Post by psusi on 2007-12-27
In your earlier post you showed that sdb has a single partition, and that sdc and sdd were the same.  Now you are saying that is not the case?

Try adding --scan to the mdadm command.

---

### Post by John Lentz on 2007-12-27
> **psusi said:**
> In your earlier post you showed that sdb has a single partition, and that sdc and sdd were the same.  Now you are saying that is not the case?

Try adding --scan to the mdadm command.

I still get the same 'no devices found for /dev/md0' when I add --scan to the mdadm cmd.  I ran sudo mdadm -A /dev/md0 --scan.   I still have my hard drive unplugged to simulate a drive failure.  When I built the array, these are the steps I took.  I used fdisk to make on big partition on each of the 3 drives.  I used :
sudo mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1

to make the array, then I ran:

sudo mkfs -t ext3 /dev/md0

The array worked fine after that.  I then changed my fstab to include:
/dev/md0     /nas    ext3    defaults   1 1

After doing that, the array starts up just fine with all 3 drives plugged in.  I can fail and restore the array with software.  Unplugging a harddrive to simulate a more realistic problem is where I am stuck.

Right now the pc is sitting with one hard drive unplugged  (for the hardware failure mode).  I'm trying to figure out what I need to do to 1) determine which drive is failed and 2) how to bring up the array to use it with 1 drive missing.

I'd appreciate any help figuring this out. 

Thank a bunch.

John

---

### Post by psusi on 2007-12-27
That is strange... it should be the same but try sudo mdadm --assemble --scan

---

### Post by John Lentz on 2007-12-27
Thank you, Thank you, Thank you.  I ran sudo mdadm --assemble --scan and it reported:
'no devices found'
'/dev/md0 has been started with 2 devices (out of 3)'

I thought it hadn't worked, but then I tried sudo mount -t ext3 /dev/md0 /nas and it mounted and is visible.  I have 2 questions though, if you don't mind.  

1) how do I tell which hard drive is the bad one?  I tried cat /proc/mdstat and it listed sdb and sdc, but not sdd.  As far as I can tell, I pulled the sata cable from the sdb hard drive.  Do they just slide up in letters?

2)  You mentioned earlier that fdisk -t should be used to set the partition properly.  Could you explain that please?

Thanks so much.

John

---

### Post by psusi on 2007-12-27
Yes, they just slide up in letters.

run sudo fdisk /dev/sdb, then at the fdisk prompt, give it the t command, select partition 1, and enter the value fd, then w to save, and q to quit.

---

### Post by John Lentz on 2007-12-27
> **psusi said:**
> Yes, they just slide up in letters.

run sudo fdisk /dev/sdb, then at the fdisk prompt, give it the t command, select partition 1, and enter the value fd, then w to save, and q to quit.

If they slide up, then how do you tell the bad drive?  Do you just put a new drive in and see if the array will run?  

Thanks again,  I really appreciate it.

John

---

### Post by psusi on 2007-12-28
What is there to tell?  You removed the bad drive... now replace it with a good drive and add it to the array.

---

### Post by John Lentz on 2007-12-28
> **psusi said:**
> What is there to tell?  You removed the bad drive... now replace it with a good drive and add it to the array.

Well, I didn't have a bad drive.  I was simulating one by unplugging the sata cable from the drive, so in this case I knew which one was "bad".  In the future, if/when a hard drive fails in the array, is there a way to tell which drive failed, since the drive letters shift?  Or is the normal practice just to pick a drive and replace it and see if the array likes it?  I'm just trying to plan my steps now, before I fill the raid with good/valuable data.

Thanks again,

John

---

### Post by fjgaude on 2007-12-28
> **John Lentz said:**
> Well, I didn't have a bad drive.  I was simulating one by unplugging the sata cable from the drive, so in this case I knew which one was "bad".  In the future, if/when a hard drive fails in the array, is there a way to tell which drive failed, since the drive letters shift?  Or is the normal practice just to pick a drive and replace it and see if the array likes it?  I'm just trying to plan my steps now, before I fill the raid with good/valuable data.

Thanks again,

John

I've asked this question several times here but received no reply. The only way I can think of is to let the array rebuild itself after a failure, then shut down the box. Pull out a drive and try to reboot. If successful then it was the bad drive, if not, put the drive back in and pull another, and so on...

---

### Post by psusi on 2007-12-28
Normally when the drives fail, they still show up, they just give errors when you try to access them, so the device names will not shift.  If it completely does not show up, then I guess you just have to pull one out and see if the system still boots.  If it does, that was the dead drive.

Or I suppose you could look at the serial number.

---

### Post by fjgaude on 2007-12-28
Really, we don't even know the device name that goes with the physical piece. There must be a clever way to know truly which drive is acting up, giving the errors. The more I think of it the bigger the head ache. <smile>

Maybe the fellow who has a logon name of "kidder" will give us a clue. If anyone knows he does. <grin>

---

### Post by psusi on 2007-12-28
mdadm will tell you the name of the device that it has decided has failed and taken offline.

---

### Post by John Lentz on 2007-12-28
Thanks for the insight.  Hopefully if one fails it will do it in a big way and my bios will show it, if not, I'll try the guess and test method.

Thanks again.

---

