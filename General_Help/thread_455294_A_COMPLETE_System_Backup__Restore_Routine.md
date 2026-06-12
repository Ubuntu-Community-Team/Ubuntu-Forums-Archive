---
title: "A COMPLETE System Backup / Restore Routine"
date: 2007-05-26
forum: General Help
---

### Post by nami on 2007-05-26
Hi

I am trying to put together a "complete" system backup and restore routine as it seems none are available.

So far I have this:

The backup process

> login as superuser
sudo su

> create backup and exclude anything you dont want to backup e.g.
tar cvpzf backup.tgz --exclude="/media/My Book" --exclude=/home/nami/Desktop/backup.tgz /

> split the backup file if too big (4Gb splits)
tar -c --tape-length=4096000 --file=backup_split.tar backup.tgz
> 
Rename the split files to backup_split_1.tar, backup_split_2.tar and so on and save onto external drive.  or you can leave the names as they are and burn them to dvd.

The restore routine:

> join the files 1 at a time by moving the first to the desktop and typing.  Then when it asks for the next file to join, replace the first file you copied onto the desktop with the second file and so on.
tar -x -M --file=split_backup.tar backup.tgz

> mount your HDD
sudo mkdir /mysystem
sudo mount /dev/sdax /mysystem

> once the files have been joined, type the following command and the system will be restored.
tar xvpzf backup.tgz -C /mysystem

[COLOR="Silver"]EDIT - no longer a problem
The problem.

How do I get the restore to work from the livecd desktop?  It seems that when you boot using a livecd, it does not mount your HDD.

Help...[/COLOR]

---

### Post by coffeecat on 2007-05-26
Method 1:

Assuming the partition you want to mount is /dev/sdax (amend as necessary)

```
sudo mkdir /mysystem
sudo mount /dev/sdax /mysystem
sudo tar blah...blah...blah
```Call /mysystem more-or-less whatever you want. Purists may object to creating a mountpoint in / preferring something in /mnt or /media, but this is a virtual filesystem in a live CD so it won't last long.

Method 2:

My preferred one - I'm a lazy blighter. :wink:

Get yourself the [SimplyMEPIS]("http://www.mepis.org/") live CD. When you boot up with that you'll find a KDE panel app towards the right with an icon that looks like three coloured cubes. It's called KwikDisk. Click on that, click on the partition you want to mount and it is automounted for you on /mnt/whatever.

Then tar away....

**Edit:** I'm assuming here that your only problem is the mounting of the hard drive. I'm full of open-mouthed admiration for your splitting and joining the tarball method, but I can't comment on whether it would work. I use tar for full system backups but I backup to an ext3 formatted usb hard drive so I don't have the 4GB limit problem.

---

### Post by raja on 2007-05-26
The systembackup and restore functionality script in Ubuntu does a pretty good job of allowing easy configuration of files to be backed up, those to be excluded, the backup schedule, etc. If you want a total system back up and recovery, I guess the easiest is to create an image of the drive (using Partimage) and then restoring from a live cd when needed.
Apart from that, the hard drive is generally mounted when you boot from the live cd, otherwise you can mount it manually.

---

### Post by coffeecat on 2007-05-26
> **raja said:**
> If you want a total system back up and recovery, I guess the easiest is to create an image of the drive (using Partimage) and then restoring from a live cd when needed.

Judging by his comment about the 4GB limit, I'm guessing that the OP is backing up to a FAT32-formatted drive and that his system is so big that it creates >4Gb images even when compressed. Will Partimage split images for you? It's been a long time since I tried it and I found it fiddly to use which is why I prefer using tar.

---

### Post by raja on 2007-05-26
I havent used partimage either - but yes, it can split the image into smaller files - see[ here]("http://www.partimage.org/Partimage-manual_Usage#How_to_save_a_partition_into_an_image_file").

---

### Post by nami on 2007-05-26
coffeecat:  I dunno if the 4GB split works or not, I havn't tried restoring it yet.

raja: where is thissystembackup and restore functionality script in Ubuntu?  How do I restore the image created with Partimage when booted with the ubuntu live cd?

coffeecat: Yes I have an external 500GB drive which I wanted to store the tar/image or the system.  I am keeping it to FAT format because I need to use the drive on microsoft os's too.

raja:  just checked that link and "ouch" :D.  i remember trying to use Partimage before and couldn't figure it out even with guides...

**EDIT - I've made some changes based on the comments and am doing a system restore "as I type" over the working system...  I hope this works. :???:**

---

### Post by raja on 2007-05-26
> **nami said:**
> coffeecat: 
raja: where is thissystembackup and restore functionality script in Ubuntu?  How do I restore the image created with Partimage when booted with the ubuntu live cd?


```
sudo aptitude install sbackup
```
For a simple introduction, look at [http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html).

raja:  just checked that link and "ouch" :D.  i remember trying to use Partimage before and couldn't figure it out even with guides...
[/QUOTE]

As far as I know it is as simple as booting in with a live cd that contains partimage, define the partition or drive to be 'imaged' and the partition to store it in. Restoring also seemed pretty straightforward.

---

### Post by nami on 2007-05-29
i tried sbackup, selected all the directories i wanted to include, set a time, and when that time came, nothing happened...

---

### Post by nami on 2007-05-29
also, when i tried what i typed in the first post on a working system, it worked perfectly, but when i removed the nvidia drivers, when tried restoring it from the backup which had the nvidia drivers, it didn't work.

---

### Post by raja on 2007-05-29
> **nami said:**
> i tried sbackup, selected all the directories i wanted to include, set a time, and when that time came, nothing happened...

Check if you have the file sbackup in /etc/cron.d.

---

### Post by ICUR2Ys on 2007-05-29
I just found this thread through a search for system backup.

Since the restores do not work I guess I have to keep looking.  Good luck.

---

### Post by ramjet_1953 on 2007-05-30
I just backup the entire HDD onto an external USB HDD, using [COLOR="Blue"]Ghost for Linux (G4L)[/COLOR].

Produces an exact 1:1 copy of my working HDD, including GRUB.

If I do have a failure, I just need swap the drives over.

I copy my /home directory onto a DVD-RW daily and do the HDD backup monthly.

Much simpler and I am 100% sure of complete backup.

Regards,
Roger :cool:

---

### Post by nami on 2007-05-31
This ghost for linux package, does it recreate the partitions too if you want to restore on a brandnew hard drive?

---

