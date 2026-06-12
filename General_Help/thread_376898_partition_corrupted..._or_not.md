---
title: "partition corrupted... or not?"
date: 2007-03-05
forum: General Help
---

### Post by Orval on 2007-03-05
I have a separate /home/ reiserfs partition. At startup the boot sequence hangs at fsck. When I do ctrl+alt+del ubuntu starts, but it cannot find my home partition.

When I boot up my knoppix live-CD, knoppix can mount the "lost" partition and read from and write to it?

Is there some way to "repair" my not-so-lost partition?

---

### Post by jimbob on 2007-03-05
What does it say when you try to mount it manually in Ubuntu?

What happens when you run fsck -r /dev/hdax  (whatever x is ...) in a terminal window?

Post a copy of your fstab.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Orval on 2007-03-06
I ran fsck from the Knoppix liveCD yesterday and it said everything is OK. No errors, nothing to replay. So the partition should be OK. fstab has not changed, so it can't be wrong, but I will post it when I get back home again.

---

### Post by Orval on 2007-03-08
I found the problem: my partitions, except for the linux partition are not mounted. When I start up in recovery mode and do 

> mount -a

to mount everything that is in /etc/fstab, the partitions are properly mounted. So  it looks like Ubuntu does not use fstab while starting.

I even reinstalled Ubuntu, but this had no effect at all. Changing the UUID's for /dev/hdxx had no effect either. 

What is going on? How can I make sure all my partitions are mounted?

---

### Post by Orval on 2007-03-08
By the way, at startup it hangs when fsck-ing the partition with my /home/, i have to continue using <ctrl><alt><del>. Using tune2fs to tell the system to check the partition every 50 times or so does not help. It just checks and hangs every startup.

I even tried the solution from [THIS]("http://ubuntuforums.org/showpost.php?p=1898964&postcount=8") post, but that did not work.

---

### Post by jimbob on 2007-03-08
On the contrary, I don't believe you want it mounted when you run fsck.

You haven't posted a copy of your fstab yet.

Let's also see the output of df -h and fdisk -l
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Orval on 2007-03-08
I will do that one of these days, when I have booted up the knoppix cd again. It is late, I am going to bed now. But thanks for your reply.

---

### Post by Orval on 2007-03-09
This is my original fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=7f1cf16c-af88-401e-9dec-0cc85ab476f0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=4343-D600  /data           vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb2
UUID=fa3a1bea-5b08-4b1a-a1e7-987c76a670e5 /home           ext3    defaults        0       2
# /dev/hda1
UUID=DEB0B628B0B606D5 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb3
UUID=720e5a55-75ea-4c40-93a2-3664da2c8f97 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


This is how I changed it in order to find a solution:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
/dev/hdb1    /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb2
/dev/hdb2    /home           ext3    defaults        0       2
# /dev/hda1
/dev/hda1    /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
/dev/hda5    /data           vfat    nouser,defaults,atime,auto,rw,dev,utf8,umask=007,gid=46 0       1
# /dev/hdb3
/dev/hdb3    none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


df -h and fdisk -l will follow in the next post.

---

### Post by Orval on 2007-03-09
df -h:

> 
Filesystem         Size      Used     Avail     Use%    Mounted on
/dev/hdb1        7.9G      2.4G     5.2G     32%       /
varrun              252M     8.0K     252M      1%      /var/run
varlock             252M         0      252M      0%     /var/lock
procbususb      10M        416K    9.6M      5%      /proc/bus/usb
udev               10M        416K    9.6M      5%     /dev
devshm            252M         0     252M      0%     /dev/shm
/dev/hdb2        137G       53G    78G       41%   /home
/dev/hda1         40G      19G      22G       46%    /media/hda1
/dev/hda5         75G       58G     18G       77%    /data



fdisk -l:

> 
Disk /dev/hdb2: 149.2 GB,  149239480320 bytes
255 heads, 63 cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hdb2 doesn't contain a valid partition table


Ah, well, it's the partition table.

But fsck gives no error.

---

### Post by Orval on 2007-03-09
OK, now I am running testdisk.

Analyse sais that the partition sector doesn't have the endmark 0xAA55.

How do I repair that?

---

### Post by Orval on 2007-03-09
Hmmm testdisk won't let me create a new partition table. Let's try gparted in Knoppix.

:(

---

### Post by Orval on 2007-03-09
Grrrr. Qparted hangs when scanning the devices. Qtparted won't let me delete the swap partition on hdb3, says it is mounted. I can delete hdb2, but then I cannot create a new one.

I think I am totally stuck now. What shall I do? What can I do? Get a new harddrive? Or is my BIOS corrupt?

---

### Post by jimbob on 2007-03-09
Early on you mentioned a reiser fs.  Where is it?

fdisk -l should have listed ALL of your partitions shown in /proc/partitions.  Is that all it gave you or did you omit the rest?

You have an hda1 and an hda5.  What happened to hda2,3 and 4?

You said you were going to use Gparted but you used qtparted instead.  I would stay away fro Qtparted if I was you.  It is a poor substitute for Gparted IMHO.

I assume you have some sort of Windows OS on hda from the looks of the partition types.

I believe you are correct - there is some form of corruption on hdb2 but the rest of your stuff is OK, right?

What I would do is to salvage as much data as possible from hdb2.  Use Gparted to determine how much data is actually on there - not how large the partition is.

When you know that you can look into shrinking and/or re-arranging partitions to create a new partition to which you can copy hdb2 as far as it will go.  All of this can be done using Gparted from the Knopper disk.

If you cannot glean enough contiguous space anywhere to copy off your data you will have to use another drive - either internal or external, then delete, recreate and format hdb2 so you can restore it from this new drive.

Sorry but that's all I can think of at this point to save your data.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Orval on 2007-03-10
> **jimbob said:**
> Early on you mentioned a reiser fs.  Where is it?

I have copied my /home from hdb2 to hda5, wiped out hdb, created new partitions, installed Edgy on hdb1 and /home on the new hdb2. As you have seen, this had no effect on the problem.

> **jimbob said:**
> fdisk -l should have listed ALL of your partitions shown in /proc/partitions.  Is that all it gave you or did you omit the rest?

I did not omit anything

> **jimbob said:**
> You have an hda1 and an hda5.  What happened to hda2,3 and 4?

Good question! The first time I installed Linux (Suse) it created hda1 and hda5. hda1 contains Windows XP, hda5 contains data. I left it the way it was and has been since september 2005.

> **jimbob said:**
> You said you were going to use Gparted but you used qtparted instead.  I would stay away fro Qtparted if I was you.  It is a poor substitute for Gparted IMHO.
That was a typo. I tried to use Gparted, but that hanged while scanning devices.

> **jimbob said:**
> I believe you are correct - there is some form of corruption on hdb2 but the rest of your stuff is OK, right?

Well, not quite. hdb2 is not corrupt. After doing a recovery start, and a mount -a, I can access everything on the partition. The data is not corrupt.


> **jimbob said:**
> What I would do is to salvage as much data as possible from hdb2.  Use Gparted to determine how much data is actually on there - not how large the partition is.

When you know that you can look into shrinking and/or re-arranging partitions to create a new partition to which you can copy hdb2 as far as it will go.  All of this can be done using Gparted from the Knopper disk.

Well, that is exactly what I did before and that had no effect.

> **jimbob said:**
> If you cannot glean enough contiguous space anywhere to copy off your data you will have to use another drive - either internal or external, then delete, recreate and format hdb2 so you can restore it from this new drive.

Sorry but that's all I can think of at this point to save your data.

Thank you for your assistance and your time.

The problem is that at startup Ubuntu wants to check the partition. It knows it is there. But fsck cannot check it and hangs. After stopping fsck with <ctrl><alt><del>, the computer starts, but it cannot find /home/ (hdb2), so I cannot log in normally with my account. hdb2 is not mounted. I can start in recovery mode.

In recovery mode, after I do a mount -a hdb2 is mounted and I can access /home/ with all files in it. The files seem not to be corrupted. At least I could access a lot of files correctly when I tried. I can start X and when in Gnome, the OS seems OK.

---

### Post by Orval on 2007-03-11
Is there anybody who can help me? Or should I just buy a new harddrive?

---

### Post by Orval on 2007-03-13
OK, a new harddrive it is.

---

### Post by Orval on 2007-03-15
Grrrr. I put in a new harddrive, installed ubuntu, but grub will not install anymore on hda (ubuntu is on hdb1, swap on hdb2 and /home on hdb3, windows is on hda1). When I install grub on hdb and modify the bios that the computer boots from hdb, grub complains that the (hdb1) partition cannot be mounted. If I try to start windows from Grub, it complains that it is not a valid executable (which is true, of course).

What is going on here?

---

### Post by Orval on 2007-03-15
I tried the live CD of Feisty and the alternate CD of edgy. They both did not work.

I tried the live CD of Kubuntu Egdy and everything worked fine...

I'll eat my shoe if I understand.

---

