---
title: "Help Making Full System Backup"
date: 2007-12-04
forum: General Help
---

### Post by zeroomegazx on 2007-12-04
I'm looking for some insight on the best way to make a full system state backup using 7.10.  The situation is as follows.  The box is going to be used as an internal website, has no tape drive, but does have access to network storage and USB storage.  I will take anything from system imaging to simple backup solutions as long as I can restore from a full cleansing of the system and can get the box up and running with little or no hassle after the restore.  I'm not super knowledgeable in Linux and don't really know what system folders should or should not be backed up either, which is why I would prefer something that could do a system state and leave me with a single restore file, but I am willing to listen and learn other ways as well, anything that can solve my problem.  Thanks a bunch!

---

### Post by Odd-rationale on 2007-12-04
Have you considered Bubakup/LVPM?

[http://lubi.sourceforge.net/bubakup.html](http://lubi.sourceforge.net/bubakup.html)

---

### Post by zeroomegazx on 2007-12-04
> **Odd-rationale said:**
> Have you considered Bubakup/LVPM?

[http://lubi.sourceforge.net/bubakup.html](http://lubi.sourceforge.net/bubakup.html)

No I haven't but I'll take a look at it right now.  Do you happen to know if you can restore the images through an Ubuntu Installation?

---

### Post by banewman on 2007-12-04
Mondo and mindi are the best linux solutions in my opinion :)

---

### Post by zeroomegazx on 2007-12-04
> **banewman said:**
> Mondo and mindi are the best linux solutions in my opinion :)

Cool thanks I'll check this one out as well

---

### Post by hoakz on 2007-12-04
If you want to back-up only documents and are a bit linux savvy take a look at the rsync command.  I use it myself to make both mirror images and incremental backups of my systems, however, I'm not aiming at restoring a working installation with one button push... I don't have the 24/7 demand in this set up :grin:

---

### Post by Odd-rationale on 2007-12-04
> **zeroomegazx said:**
> No I haven't but I'll take a look at it right now.  Do you happen to know if you can restore the images through an Ubuntu Installation?
No. Unfortunately, you need Bubakup/LVPM in order to restore.

---

### Post by zeroomegazx on 2007-12-05
Is there an easier way to backup my system, perhaps using Tar?  I saw some threads regarding it but I am not sure that it is going to fit my need, just wondering if anyone has had experience with it.

---

### Post by mannheim on 2007-12-05
> **zeroomegazx said:**
> Is there an easier way to backup my system, perhaps using Tar?  I saw some threads regarding it but I am not sure that it is going to fit my need, just wondering if anyone has had experience with it.

You can use tar or rsync in a quite straightforward way. Assuming you have a big external USB hard disk mounted at /media/usb-disk (or something) you can do:

```
sudo rsync -a -x /  /media/usb-disk/my-backup
```

This will create a mirror of everything under "/" to a directory "my-backup" on the usb-disk. The option "-a" means "--archive", which tells rsync to preserve permissions, soft links, special files etcetera. The option "-x" means "don't descend into mounted file-systems". This means that rsync won't try to backup the contents of "/media/cdrom", but it also means it won't back up /home if you have a separate partition for /home. No compression is done. You can bring the mirror up to date later by repeating the command, but adding the "--delete" option to rsync (which tells it to remove files in the mirror which are no longer on the source).

Making a backup is always the easy part. Restoring is the interesting bit. As long as the layout of your partitions hasn't changed and nothing has been reformatted, you can restore by doing:
[LIST=1]
[*]Boot from a live CD
[*]Mount the usual root partion at /mnt/target
[*]Mount the usb disk at /media/usb-disk
[*]Restore with "rsync -a --delete /media/usb-disk/my-backup/ /mnt/target". (The trailing slash after "my-backup" is needed.)
[/LIST]

If a reformat has been done, you need to worry about three additional things:
[LIST=1]
[*]You need to reinstall grub
[*]The file /etc/fstab in recent versions refers to partitions by their "UUID", which will have changed if you reformat. You need to edit the copy of /etc/fstab before rebooting.
[*]Ditto for /boot/grub/menu.lst
[/LIST]

A slow but reliable workaround for the last three points is simply to restore a fresh copy of Ubuntu on the newly-formatted disk, save a copy of the /etc/fstab and /boot/grub/menu.lst files on some removable media, then do the restore as above, and finally copy back the /etc/fstab and /boot/grub/menu.lst from the removable media before rebooting.

---

### Post by psusi on 2007-12-05
The simplest way ( which is not the same as easiest ) is to just use tar.  I have a cron job set to do a nightly incremental backup on my server and a weekly full backup.  

My full backup script looks like this:

#shut down servers to get a clean backup
/etc/init.d/apache2 stop
/etc/init.d/mysql stop

#clear the snapshot to force a full backup
rm -f /backup/backup.snapshot
#do the backup
tar czf /backup/`date +%F`-full.tar.gz --exclude='/backup/*' --exclude='/proc/*' --exclude='/sys/*' --exclude='/tmp/*' --exclude='/dev/*' --exclude='/var/cache/*' -g/backup/backup.snapshot

#restart the servers
/etc/init.d/mysql start
/etc/init.d/apache2 start

The daily script is the same, but without the rm and '-daily.tar.gz' instead of '-full.tar.gz'.  These scripts generate a nice pile of weekly backups in /backup named something like "2007-11-25-full.tar.gz" and "2007-11-26-daily.tar.gz".

---

### Post by zeroomegazx on 2007-12-05
> **psusi said:**
> The simplest way ( which is not the same as easiest ) is to just use tar.  I have a cron job set to do a nightly incremental backup on my server and a weekly full backup.  

My full backup script looks like this:

#shut down servers to get a clean backup
/etc/init.d/apache2 stop
/etc/init.d/mysql stop

#clear the snapshot to force a full backup
rm -f /backup/backup.snapshot
#do the backup
tar czf /backup/`date +%F`-full.tar.gz --exclude='/backup/*' --exclude='/proc/*' --exclude='/sys/*' --exclude='/tmp/*' --exclude='/dev/*' --exclude='/var/cache/*' -g/backup/backup.snapshot

#restart the servers
/etc/init.d/mysql start
/etc/init.d/apache2 start

The daily script is the same, but without the rm and '-daily.tar.gz' instead of '-full.tar.gz'.  These scripts generate a nice pile of weekly backups in /backup named something like "2007-11-25-full.tar.gz" and "2007-11-26-daily.tar.gz".

Ok how would i restore this?

---

### Post by zeroomegazx on 2007-12-05
> **mannheim said:**
> You can use tar or rsync in a quite straightforward way. Assuming you have a big external USB hard disk mounted at /media/usb-disk (or something) you can do:

```
sudo rsync -a -x /  /media/usb-disk/my-backup
```

This will create a mirror of everything under "/" to a directory "my-backup" on the usb-disk. The option "-a" means "--archive", which tells rsync to preserve permissions, soft links, special files etcetera. The option "-x" means "don't descend into mounted file-systems". This means that rsync won't try to backup the contents of "/media/cdrom", but it also means it won't back up /home if you have a separate partition for /home. No compression is done. You can bring the mirror up to date later by repeating the command, but adding the "--delete" option to rsync (which tells it to remove files in the mirror which are no longer on the source).

Making a backup is always the easy part. Restoring is the interesting bit. As long as the layout of your partitions hasn't changed and nothing has been reformatted, you can restore by doing:
[LIST=1]
[*]Boot from a live CD
[*]Mount the usual root partion at /mnt/target
[*]Mount the usb disk at /media/usb-disk
[*]Restore with "rsync -a --delete /media/usb-disk/my-backup/ /mnt/target". (The trailing slash after "my-backup" is needed.)
[/LIST]

If a reformat has been done, you need to worry about three additional things:
[LIST=1]
[*]You need to reinstall grub
[*]The file /etc/fstab in recent versions refers to partitions by their "UUID", which will have changed if you reformat. You need to edit the copy of /etc/fstab before rebooting.
[*]Ditto for /boot/grub/menu.lst
[/LIST]

A slow but reliable workaround for the last three points is simply to restore a fresh copy of Ubuntu on the newly-formatted disk, save a copy of the /etc/fstab and /boot/grub/menu.lst files on some removable media, then do the restore as above, and finally copy back the /etc/fstab and /boot/grub/menu.lst from the removable media before rebooting.

OK I'll give this a try as well, thanks for the idea

---

### Post by psusi on 2007-12-05
> **zeroomegazx said:**
> Ok how would i restore this?

Boot from something like the livecd, fdisk and format the partition(s) as needed, mount them, and extract the tarballs ( tar xzf backup.tar.gz ).  Start with the full, then repeat for each daily backup since the full.  Once all the files are restored, reinstall grub to make the disk bootable.

---

