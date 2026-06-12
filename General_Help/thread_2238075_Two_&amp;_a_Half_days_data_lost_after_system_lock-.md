---
title: "Two &amp; a Half days data lost after system lock-up :shock:"
date: 2014-08-05
forum: General Help
---

### Post by netsurfau on 2014-08-05
On Sunday I added a second 500Gb drive to my system, and the extended  /dev/sda to use all the space on first HD.

I did this by using Clonezilla Live & gParted Live on a USB stick.  I first used Clonezilla to back up my /dev/sda, I then used gParted to increase it's size to use all the unallocated space on the drive.  I did the same on /dev/sdb as Clonezilla had only created a partition the same size as the one backed up.

When I got up this morning (08:00 Australian Eastern Standard Time), I turned on my monitor & found that my system was frozen solid.  I used the Reset function on the computer & when it rebooted I found that it had reverted to where it was just before I made all the changes.

When I look at the drives using GParted, /dev/sda is now almost completely full with only about 11.44GB free space left, and /dev/sdb looks wrong (can't think of any other way to describe it).

Both drives are showing their mount point as " / ", which I know is not how they should be.

Is there any way to retrieve the missing data and get my drive back to where they should be?

Image 1 - GParted /dev/sda

[ATTACH=CONFIG]255276[/ATTACH]

Image 2 - GParted /dev/sdb

[ATTACH=CONFIG]255277[/ATTACH]

---

### Post by yancek on 2014-08-05
Clonezilla has several options.  You can clone an entire drive from one to another of equal or larger size.
You can also clone one partition to another partition on the same or another drive.
You can also clone and create an image file of it which can later be installed.

You seem to be saying you cloned the entire sda drive and also the sdb drive??  Or did you clone sda and put it on sdb?

> Both drives are showing their mount point as " / ", which I know is not how they should be.

If you cloned the system or partition that would be expected.  One would be a copy of the other.  Were you just meaning to back up your data or did you actually want to clone the entire system?  Can you boot anything or are you using some live medium?  I'm not sure what missing data you mean?  There seems to be a lot of data there but I guess you can't access it?

---

### Post by oldfred on 2014-08-06
If a total clone you may have duplicated the UUIDs and you cannot have that.

Post this.
       sudo blkid -c /dev/null -o list

---

### Post by netsurfau on 2014-08-06
@yancek,
I cloned sda as a backup before resizing it.

@oldfred,

That command returned:

luke@Quad-Core:~$ sudo blkid -c /dev/null -o list
[sudo] password for luke: 
device     fs_type label    mount point    UUID
------------------------------------------------------------------------------
/dev/sda1  ext4             (not mounted)  43908c55-e220-4ea7-acf4-01732be278b9
/dev/sda3  swap             <swap>         8b50546d-9b1b-47b8-93e9-431595240d9c
/dev/sdb1  ext4             /              43908c55-e220-4ea7-acf4-01732be278b9


Seeing  that sda1 isn't mounted explains where all my data went, and I can see that they're both showing the same UUID.
Do you know why sda1 would have (I think) more than doubled the amount of data on it?

I looked at the link you posted, it referred to UEFI Installing.  I didn't want the second drive to be bootable, it's main purpose
is to be an additional data drive, as well as a point for storing back-ups of my /home directory.

---

### Post by oldfred on 2014-08-06
The link to UEFI is in my signature, so it always is posted. Was not specific to you. But I do believe in having a working install in every data drive also.

Not sure what happens if you have duplicate UUID, someone posted that some data went into each drive and then system would be corrupted.

You need to change UUID of one or the other. If copy is just data that would be easier as otherwise you have to update fstab and reinstall grub to update all the internal references to correct new UUID.

       Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX

If you just wanted a copy of the data, something like rsync may have been better. I use resync script to backup /home and some other data. 

I do not use Knoppix, and now with SSD having my working installs, I have my test installs of Ubuntu in my data drive. But every drive has a bootable system, including most flash drives.

 Creating a Dedicated Knoppix Partition for large drives
[URL="http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm"]http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm

[/URL] Oldfred's list of stuff to backup May 2011:
[URL="http://ubuntuforums.org/showthread.php?t=1748541"]http://ubuntuforums.org/showthread.php?t=1748541
      [/URL]
 Some files to exclude from /home backup - post #8 by  Paddy Landau
[URL="http://ubuntuforums.org/showthread.php?t=1883834"]http://ubuntuforums.org/showthread.php?t=1883834
      [/URL]
 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

    [URL="http://ubuntuforums.org/showthread.php?t=1883834"]
[/URL]

    [URL="http://ubuntuforums.org/showthread.php?t=1748541"]
[/URL]

[URL="http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm"]
[/URL]

---

### Post by netsurf on 2014-09-13
@oldfred,

Sorry for delay in getting back to you, health isn't the greatest.

I ended up using the bootable version of gParted again, and was able to change the UUID on the second drive,  So that problem was sorted.
Still lost a couple of days data, but I can live with that.

Thanks for your help.

Luke

---

