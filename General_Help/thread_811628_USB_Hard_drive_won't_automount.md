---
title: "USB Hard drive won't automount"
date: 2008-05-29
forum: General Help
---

### Post by powerpleb on 2008-05-29
I have a Maxtor external USB hard disk that I'm using for backup.
I want it to automount every time I boot the system but it won't work.

This is what I have in my fstab:
> # /dev/sdc1 - external backup drive
UUID=1b4d1bc0-bd0a-4410-8e10-16dd10506467   /mnt/maxtor   ext3    defaults 0 0 

When it does boot up if I then do... > sudo mount -a
...it mounts. But it never automounts during bootup.

I first had the pass setting in fstab on 2 and it would error during bootup saying it couldn't check the filesystem. When I pressed CTRL-D and continued booting it automounted. So I changed the pass setting to 0 and now I don't get the error but it doesn't mount.

This is blkid output: 
> /dev/sdc1: LABEL="maxtor" UUID="1b4d1bc0-bd0a-4410-8e10-16dd10506467" TYPE="ext3" 


This is mount -l output after I've successfully mounted it with mount -a:
> /dev/sdc1 on /mnt/maxtor type ext3 (rw) [maxtor]

This is the /var/log/fsck/checkfs after it errors:
> Log of fsck -C3 -R -A -a 
Thu May 29 23:28:31 2008

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=1b4d1bc0-bd0a-4410-8e10-16dd10506467'

storage: clean, 14712/15540224 files, 9422903/62151460 blocks
fsck died with exit status 8

Thu May 29 23:28:32 2008
----------------

---

### Post by geo909 on 2008-05-29
Ok, it's very possible that I will say something stupid, but I'll try;

Try to comment any line in fstab related to your external disk.
Then reboot with your disk plugged in..
Does it (auto)mount? I think it should be..
In ubuntu all the USB drives work like that, I think, they automount
and do not need to have entries in fstab.


If it doesn't work, try to install pysdm from synaptic (PYthon Storage Device Manager). It's a little tool with a friendly GUI that helps you manage the way you handle your hard disks. It actually writes lines in fstab but you only have to tick boxes, it's really easy. It also has options about automounting and stuff.

EDIT: Did you do anything with gparted before your problem appeared? I see your drive is ext3 so I guess it was NTFS and you formatted it. In case you used gparted, did you have any crashes? Can you check if your other USB devices automount on startup if they are plugged in?

---

### Post by powerpleb on 2008-05-29
That sort of worked except that it didn't actually automount. An icon showed up in 'Computer' and when I clicked it the disk then mounted.

> EDIT: Did you do anything with gparted before your problem appeared? I see your drive is ext3 so I guess it was NTFS and you formatted it. In case you used gparted, did you have any crashes? Can you check if your other USB devices automount on startup if they are plugged in?

That's true, I formatted it to ext3 from NTFS recently using gparted. I didn't crash, as far as I could tell everything went fine. Other USB devices (USB pens etc) don't automount either, but I can click on their icons in 'Computer' but they are all ext3 or Reiserfs. Strange thing is that it always automounted when it was NTFS. So, like you said, maybe I shouldn't have messed with fstab. Or maybe I should have left it as NTFS. But I wasn't sure if rsync would work with it.

Anyway, I've found a different way around it that I hope works.
As I'm using the USB hard drive for backup only and don't intend to access it unless I'm recovering something, I've come to the conclusion that I don't really need it to automount or to be on my desktop. In fact it's probably safer if nobody can see it at all.

So I put 'noauto' in fstab:

> /dev/sdc1   /mnt/maxtor   ext3    noauto,defaults 1 0

then in my backup script I put the mount and umount commands so it looks like this:
> 
#!/bin/sh
# /usr/local/bin/rsync.sh
#
# - This script backs up users Documents folders to the internal drive 
# then backs up the internal drive to the external USB drive.
# 
# /home/user1/Documents (small)
# /home/user2/Documents (very small)
# /media/sdb5 (very large)
# 
# - must be executed by root as it mounts the external drive
# - other dirs (video, tgz, etc.) must be updated by hand
# 
echo ""
echo "BACKUP SCRIPT: Backs up contents of /dev/sdb5 to /dev/sdc1"
echo "**********************************************************"
echo ""
echo "(1) Mounting the external hard disk..."
echo ""
mount -vt ext3 /dev/sdc1 /mnt/maxtor
echo ""
echo ""
echo "(2) Backing up docs..."
echo ""
rsync -urt --progress --delete /home/user1/Documents /media/sdb5/user1
rsync -urt --progress --delete /home/user2/Documents /media/sdb5/user2
echo ""
echo ""
echo "(3) Backing up other stuff..."
echo ""
rsync -urt --progress --delete /media/sdb5/ /mnt/maxtor/
echo ""
echo ""
echo "(4) Unmounting the external hard disk..."
echo ""
umount -v /dev/sdc1
echo ""
echo "All done."
echo ""

I tested the script and it works well.

So finally I put the script in /etc/anacrontab in order to schedule it to happen every day, 30 minutes after I first power up the computer.

> 
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1	5	cron.daily	 nice run-parts --report /etc/cron.daily
7	10	cron.weekly	 nice run-parts --report /etc/cron.weekly
@monthly	15	cron.monthly nice run-parts --report /etc/cron.monthly

#rsync backup tasks
1       30      System_backup    /usr/local/bin/rsync.sh


I have no idea if this bit will work so I guess I just have to wait until tomorrow and see. My main concern is that anacron will try to implement the task during bootup when the USB modules are not properly loaded and it can't mount the drive. The result would be that the '/mnt/maxtor' directory on my '/' partition will fill with these files and consume all the disk space.

---

### Post by geo909 on 2008-05-30
> **powerpleb said:**
> That sort of worked except that it didn't actually automount. An icon showed up in 'Computer' and when I clicked it the disk then mounted.

Well, I'd prefer it that way!


[QUOTE]
That's true, I formatted it to ext3 from NTFS recently using gparted. I didn't crash, as far as I could tell everything went fine. Other USB devices (USB pens etc) don't automount either
[\QUOTE]

Just check if gparted has left a file like:
```
/usr/share/hal/fdi/policy/gparted-disable-automount.fdi
```
If this is the case, then if you delete it I guess that you will have your devices automounted.. That was the solution in [another thread]("http://ubuntuforums.org/showthread.php?t=545661").


[QUOTE]
 So, like you said, maybe I shouldn't have messed with fstab. Or maybe I should have left it as NTFS. But I wasn't sure if rsync would work with it.
[\QUOTE]
I have an external disk in ext3 too for backup purposes. I had the ext3/ntfs dillema too but since I did a lot of backing up and I included big files (ISOs,videos etc) NTFS was getting really fragmented. People here suggested to turn it to ext3 because it's not getting fragmented. Well, that's not completely true but it's true that it's much better on this issue. 

 Rsync has absolutely no problem with ntfs.

 For back up, I use rsync too, but i needed to handle a couple of files in a different way. There is another similar tool, named unison. Maybe you'd want to check it out, too. 

 Hope your cron thing works. I never used cron, so I can't tell..

---

### Post by powerpleb on 2008-05-30
```
/usr/share/hal/fdi/policy/gparted-disable-automount.fdi
```

I couldn't find this file. 
But it doesn't matter as I agree that it's better when USB pens and HDDs don't automount when you turn your system on. What if some scallywag comes and yanks them out without thinking?

So with some help from [this page]("http://www.cyberciti.biz/faq/shell-how-to-determine-the-exit-status-of-linux-and-unix-command/") I've tweaked my script a little:
```

#!/bin/sh
# /usr/local/bin/rsync.sh
#
# - This script backs up users Documents folders to the internal drive then backs up the internal drive to the external USB drive.
# - must be executed by root as it mounts the external drive
# 
echo ""
echo "BACKUP SCRIPT: Backs up contents of /dev/sdb5 to Maxtor external hard disk"
echo ""
echo "[`date`] rsync backup tasks starting" >> /var/log/rsync.log
echo ""
echo "(1) Mounting the external hard disk..."
echo ""
mount -vt ext3 LABEL=maxtor /mnt/maxtor > /dev/null
chkmnt=$?
if [ $chkmnt -eq 0 ] ; then
  echo ""
  echo ""
  echo "(2) Backing up docs..."
  echo ""
  rsync -urt --progress --delete /home/user1/Documents /media/sdb5/user1
  rsync -urt --progress --delete /home/user2/Documents /media/sdb5/user2
  echo ""
  echo ""
  echo "(3) Backing up other stuff..."
  echo ""
  rsync -urt --progress --delete /media/sdb5/ /mnt/maxtor/
  echo ""
  echo ""
  echo "(4) Unmounting the external hard disk..."
  echo ""
  umount -v /mnt/maxtor
  echo ""
  ret_val=$?
  echo "[`date`] Backup was successful. Exit status $ret_val" >> /var/log/rsync.log
  echo "All done."
  echo ""
else
  echo ""
  echo ""
  echo "External hard disk did not mount or is in use. Exiting..." 
  echo "[`date`] Drive did not mount or was already mounted! Backup aborted. Mount failed with exit status $chkmnt" >> /var/log/rsync.log
fi
```
This way if the mount isn't successful or the disk is already mounted (which probably means I'm using it) the backup process is aborted. I did this because yesterday I inserted another pen drive and it took the place /dev/sdc1 and pushed [maxtor] to /dev/sdd1. The pendrive failed to mount (not ext3) and the '/mnt/maxtor' directory on my Filesystem partition began to fill with files. ](*,)

So I guess cron works.:)

---

### Post by geo909 on 2008-05-31
Good one! Glad you did your lob.
Btw I think I will use your script for my backup, it's better!

---

### Post by a_px on 2009-02-19
Hi, I have been reading this thread with interest as I have a very similar problem. I also have just bought a Maxtor 1TB external USB hard drive, and also reformatted it to ext3 - it came with NTFS. I can mount the drive manually and read & write to it no problem.

The problem is (feel free to tell me this is stupid) I would like to use this drive as my home directory & would therefore need to automount at boot time (explanation below). I was concerned about data throughput speeds via usb, but I'm getting about 28M Bytes/s which seems adequate for my purposes.

I recently bought new PC hardware as my old one was groaning. My old PC had my home directory on a separate drive & I intended to just install the drive in the new PC, only to discover that everything was SATA not IDE, and there ain't much physical space to put another drive anyway - which is why I went for the external USB drive. Looking back, I probably should have bought one with a SATA interface & fitted an external SATA socket on the PC, but I didn't!

I have put an entry in fstab as follows:

```
# Entry for /dev/sdb1
UUID=ecfabd09-7ce8-4c5d-8422-5c4ba61ac247 /home/disk ext3 defaults,auto,rw 0 0
```

What seems to happen is this initially comes up automounted (first reboot after manual mounting). Second reboot - drive is not automounted on /home/disk any longer but automounts on /media/disk with desktop icon and also decides its device name is now /dev/sdf1 as opposed to /dev/sdb1

It seems that maybe I need to prevent the drive being recognised as a removable drive in order to stop it mounting this way. Does that sound reasonable & any ideas how I can do it?

Alan

---

