---
title: "DDrescue from Ubuntu Live CD logfile location"
date: 2014-05-02
forum: General Help
---

### Post by piet3 on 2014-05-02
Hi,

I'm trying to run ddrescue from the Live Rescue Remix CD. The goal is to try and recover as much data as possible from a Seagate 1TB drive that has suffered from a lost partition in Windows. The drive does not have an OS and is purely data. Destination drive is also a Seagate 1TB. The intention is to do disk to disk and not an image file since I would like to get the whole disks info.

Background: sudo lshw -C disk -short

/dev/sda  disk  1TB SCSI Disk
/dev/cdrom
/dev/sdb disk 1TB ST31000528AS
/dev/sdc disk 500GB ST 3500418AS

sda is the faulty disk
sdb is the destination disk
sdc is a blank drive I was hoping to use for the logfile location. but I have no idea how to get ddrescue to send it there
I'm running ddrescue from the Live CD with the following:


The command I'm running is:

sudo ddrescue -f -n /dev/sda /dev/sdb logfile

This runs for a few minutes and ends in this error:

Error writing logfile logfile: No space left on device. 

I'm assuming it is keeping the logfile in memory since I'm booting of a CD and this is filled up.  Since it is now weekend I have given it the same command minus the logfile to see how far it gets.

Any pointers on how I can point the logfile to the sdc location?

---

### Post by TheFu on 2014-05-02
Is there a Linux file system partition on sdc? It is mounted?

So ... assuming it is sdc1, ext4, and mounted on /mnt the command would be ....

```
sudo ddrescue  /dev/sda /dev/sdb /mnt/logfile
```
Currently, the command being used it trying to write to whatever the CWD is ... probably using a tempfs from the liveCD.

---

### Post by piet3 on 2014-05-04
Hi TheFu, thanks for the reply.

No sdc is a blank drive, unformatted. Being new at Linux it looks like I need to do the following:
sudo fdisk /dev/sdc
option n for new partition
w to write the change and q to quit.

To create the filesystem. I assume sdc refers to the drvie, sdc1 would then be the partition? I'm a little confused because it seems from some posts that sdc1 refers to the partition and when creating the filesystem it should be sdc2?

sudo makefs.ext4 /dev/sdc1

Regards!

---

### Post by TheFu on 2014-05-04
So ... you made statements, but didn't ask any questions.  It is best to clearly as a question to get help.

fdisk is deprecated. Best to use gparted or parted instead. This is about GPT and 2+TB HDD support, but it is best to just get used to it now.

Time to learn more about disks, partitions, and file systems. Google is your friend.  While you are at it, learn a little about MBR vs GPT.

It is considered "bad form" to directly call the mkfs.{insert fs here} programs directly.  Use **mkfs -t {insert fs type here}** instead.  Installation and gparted make this easy ... until you grow into using LVM and/or RAID.

sdc is the whole drive.
sdc1 is the 1st primary partition.
sdc2 is the 2st primary partition.
and so on.  Partition numbers do NOT need to be in order or laid out in sequence on the disk either.
Now it gets tricky - if an MBR partition table is used, there are strict limits and rules that must be followed manually. Some OSes can boot from "logical partitions", others cannot. Read up on this.  OTOH, if a GPT partition table is used, then things are simpler. All partitions are primary and the limits won't matter to us for many years.  I much prefer GPT partitioning over MBR for a number of technical reasons.  Of course, Microsoft and hardware may prevent using GPT, so there are some conditions where it cannot be used as the boot device.  

File systems go into partitions, 95% of the time for home and desktop users. On servers, things can become very complicated.

BTW, help.ubuntu.com has lots of guides for the stuff you are likely to want to learn. Be careful reading random blogs looking for Linux help. I've noticed that many of those blogs are written by a noob who believes he just figured something out, because it worked.  Often, those articles are NOT the suggested way to do it and have many extra steps that just aren't needed. Over time, you'll start to figure out which websites can be trusted - usually there is a tie-in to Ubuntu or Canonical for the best guides.  askubuntu.com, howtoforge.com, and help.ubuntu.com are reputable.  Some of the blueocean stuff is good too.

As with all things, the more you do it, the more comfortable you will become.  Screwing around with partitions can be scary and can completely destroy a running OS. It is best to have a 100%, complete, recoverable, backup ready for when you screw up. We all do from time to time.

---

### Post by piet3 on 2014-05-04
Thanks again for the feedback. Indeed I did not formulate a question properly, but hoped that I was on the right track with what I've read from various blogs. One included instructions on ddrescue but as the author stated some "obvious" steps are excluded. Makes for a particular difficult read if you don't normally 'mount' drives as I'm not doing in Windows.

I'll have a read through some of the forums you listed tonight and should be able to do some more troubleshooting on my defective drive tomorrow.

---

### Post by piet3 on 2014-05-14
I have been busy with a few other items but can now try to continue. I have also cleared a 3rd drive to try and use as a logfile location.

From sudo lshw -c disk -short I get the following
/dev/cdrom
/dev/sda 1TB ST31000528AS (target)
/dev/sdb 500GB WDC (logfile location)
/dev/sdc 1TB SCSI Disk (faulty source)

I created an ext4 filesystem with a gparted live cd on sdb but I'm not sure that I did it correctly since I'm unable to mount it. 
sudo parted /dev/sdb
print

Result:
Model: ATA WDC WD5000 etc
Number    Start   End     Size      System
1         1049kb   500GB   500GB   ext4

Would I need to create a directory to point the logfile to?
Should I be concerned that Testdisk can not find a partition on sdc, even with a Deep Search?

Regards
Piet

---

### Post by TheFu on 2014-05-14
Steps to using a drive
a) partition
b) create a file system
c) mount the file system to a directory
d) correct the permissions on the mounted directory, as needed. Normally, root.root is the default and NOT what users want for extra storage.

---

### Post by piet3 on 2014-05-15
Thanks,

I have managed to start ddrescue as follows:

sudo ddrescue -f -n /dev/sdc /dev/sda /mnt/logfile

This has started to run  with the following output:
rescued 0 B errsize 1TB current rate 0 B/s and then a whole list of information

From this it does not seem that it has rescued anything yet and is constantly splitting failed blocks. I will let it run unless this is not normal and I should try to do something else first that would improve the success rate?

---

