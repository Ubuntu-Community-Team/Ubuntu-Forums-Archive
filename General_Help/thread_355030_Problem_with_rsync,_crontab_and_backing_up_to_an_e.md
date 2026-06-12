---
title: "Problem with rsync, crontab and backing up to an external hard-drive"
date: 2007-02-06
forum: General Help
---

### Post by AndyCooll on 2007-02-06
Hi folks,

I'm having a real problem with rsync, since I cannot seem to auto-backup a couple of folders. These are sat on my file server and I want to make a straight copy of them on my external hard-drive (which is also attached to the file-server). It worked first time round so now I have a copy of the folders. However they are now not updating and I'm not sure where I'm going wrong.

I've put the following lines in the "servers" root crontab (sudo crontab -e):
```
00 3 * * 2 /usr/bin/rsync -arc --delete /user /media/usbdisk/user_backup
00 5 * * 2 /usr/bin/rsync -arc --delete /share /media/usbdisk/share_backup
```

If I login to the server the "usbdisk" displays on the desktop and in /media. And if I type "ls /media" it displays correctly too. 

Interesting enough, if I ssh in to the server /media/usbdisk doesn't appear if I type "ls /media" (even though I know it should be recognised).

So ...where am I going wrong? Are the crontab lines correct? Any guidance would be appreciated.

:cool:

---

### Post by WW on 2007-02-06
The rsync commands in the crontab look OK, assuming you want the backup to run once each week. (Minor point: the "r" in -arc is redundant, since "a" implies "r".)

You said
> Interesting enough, if I ssh in to the server /media/usbdisk doesn't appear if I type "ls /media" (even though I know it should be recognised).
You should figure out what is going on here.  This may be why your backup is not working.

---

### Post by AndyCooll on 2007-02-07
Thanks for the reply. Yes, once a week is exactly how often I want these folders to be backed up.

Since my crontab commands are ok, anyone have any ideas why my external drive isn't always available via the command line?

:cool:

---

### Post by mmathur on 2007-11-08
Does you USB drive shut down or spin down the disk to put in a sleep mode and potentially the Disk is not getting 'woken' up or takes some time to wake up/become active when you use SSH and try to access the drive.  Just a random idea, but not sure if this is on the mark.

---

### Post by zman58 on 2007-11-14
Here is what I believe is happening and what you might try to get it working. I have been experimenting in this area and I am using this approach...

As you already have noticed...If you powerup or plug in your usb drive while logged into the desktop it should become visible to you. It automounts and provides access to the login account. After you log out it is automatically unmounted. When you log in via command line or ssh it does not automount (not X server account login). So if you want access from it via ssh, you would have to mount it eplicitly.

To be able to mount it explicitly, put a device entry in /etc/fstab for it. The mountpoint that you use in fstab will be where the usb drive device gets mounted to (i.e. /media/usb_backup_drive). This will allow you to be able to mount it explicitly at the command line. For example...

   mount /media/usb_backup_drive/

...or unmount it

   umount /media/usb_backup_drive/

Now that you have access to the USB drive from command line, you should create a shell script (i.e. backup_job)  that mounts, calls rsync, then unmounts the USB drive.

You will then need to call the backup_job script in the root cron. Run "sudo bash" to get to root prompt. Run "crontab -e" to edit root cron jobs to insert the backup_job script invocation. For example to run backup job each day at 2.30 AM...

30 2 *** /root/backup_job >/var/log/backup_job.log

Notice that I did not make any assumptions about environment. When cron runs the root job it looks in the root home which is /root. This is slightly different than normal users (/home/username/). This confused me at first, until I realized what was happening.

As long as the usb drive is not mounted and while you are logged into the desktop, you could switch it off then back on again and it should automount for the desktop account and provide access to it from the desktop account. BUT make sure it is **not already mounted** first before switching it off!!! (If the backup job is still running it will be mounted and owned by root.) If you enter the command "mount" on the command line it will show you all mounted volumes so you could tell if the usb drive was mounted.

Alternatively you could hard "fix" the USB drive as part of the system and have it mounted always. I think you can do that with the fstab entry. Sorry, no details on that. I am not doing this presently on my system, but might set it up that way.

Although I did not provide all details, I hope it is enough to get you up and running.

Cheers and have fun...

---

### Post by zman58 on 2007-11-19
I will post my backup_job shell script. It ran successfully last night and appears to be working properly. It backs up all home directories to an external USB drive using rsync. It mounts the USB drive, backs up the files, then unmounts the USB drive.

Normally, the USB drive remains on. During backups it shows up on users desktop but they can not write to it since it was mounted by root. Backup runs at an off time on this system (3:00 AM) so it really is not an issue for users.

To allow backups to the drive you need to place a single file on the drive root. A marker so to speak. This avoids the situation of writing to a mount point that is not really mounted. If the marker is not present, then the backup job will not run.

If a user needs to be able to read or write to the backup USB drive, they just switch the USB drive off, then back on again, it mounts for them. Afterwards they can read and write to it. Of course they should not switch it off in the middle of a backup when it is mounted by root during nightly backup processing. My crontab entry for root looks like this.

1 3 * * * bin/backup_job >/root/backup_job_cron.log

Here is the backup_job script...

```
#!/bin/sh
#
# backup_job
#
# This shell script provides an automated backup process for backing up a
# system to an external hard drive. The script is designed to be run by root
# for the purpose of backing up data in a given directory and below. The script
# mounts to the device, backs up files to it using rsync, then unmounts the
# device. The backup drive must have a special file on it before this script
# will use it for a backup media target.
#
# Author: Kenneth W. Zahorec
# Website: http://home.neo.rr.com/zahorec/
#
# History:
#
# backup_job version 1.1 - 2007-11-18
#	Corrected check for root. Use $LOGNAME instead of $USER
#
# backup_job version 1.0 - initial version 
#
# License: GNU Public Licence version 3. GPL v3
# Licence text can be found at the Free Software Foudation website.
#	http://www.fsf.org/
#
###################################################################
# 
# USAGE:
# A mountpoint in the system must be established for the USB drive.
# As root create a mountpoint and add an entry into /etc/fstab such
# as below...
# device     mountpoint          filesystem    options
# /dev/sdb1  /media/usb_backup   auto          rw,user,noauto 0 0
#
# The script can be invoked directly as root or run at regular intervals
# by entry into the root crontab.
####################################################################
# SCRIPT variables...
# backup_drive_id - A file named this must exist in the root of the backup
# drive to designate it as a "real" backup drive. We do not want to accidently
# back up to a local directory!
backup_drive_id=gatekeeper_backup_drive

# This defines the mount point in the system for the backup drive.
backup_mount_point=/media/usb_backup

# The directory that will be recursively backed up
backup_dir=/home

# The directory that will be the target for the backup data
backup_target=BACKUP_DATA

# Begin script processing here...

echo "$0: we will attempt to backup all files and directories at and below $backup_dir to $backup_mount_point..."

# Make sure we are being run as root
if [ "x$LOGNAME" != "xroot" ]
then
	echo "$0 ERROR: Script invoked by $USER. This script should be run by root."
	exit 1
fi

# Warn if backup drive is already mounted. This could be a problem if the
# wrong drive is mounted. Normal condition at this point is unmounted drive.
if grep -q $backup_mount_point /etc/mtab 
then
	echo "$0 WARNING: $backup_mount_point is already mounted!"
else
	# attempt to mount backup drive
	if mount $backup_mount_point
	then
		echo "$0: $backup_mount_point successfully mounted..."
	else
		echo "$0: ERROR: Unable to mount USB drive at $backup_mount_point"
		exit 1
	fi
fi

# make sure we have a positively identified backup drive mounted...
if [ ! -f $backup_mount_point/$backup_drive_id ]
then
	echo "$0: ERROR: The mounted backup drive was not properly identified with id file \"$backup_drive_id\""
	exit 1
else
	echo "$0: Backup drive properly identified with id file \"$backup_drive_id\""
fi

# everything looks good to this point. Invoke rsync to perform the backup operation...
# r-recursive l-copySymlinks t-preserveTimes --modify-window=1sec(timestamp resolution) --dry-run(optional)
echo "$0: rsync will now be called..."
rsync -rlvt --exclude=.* --modify-window=1 $backup_dir $backup_mount_point/$backup_target

# unmounted the backup drive ...
if umount $backup_mount_point
then
	echo "$0: $backup_mount_point successfully unmounted."
else
	echo "$0 WARNING: $backup_mount_point failed to unmount!"
fi

# we are done...
echo "$0: this script has completed!"
exit 0

```

I hope this helps out. Change it to suit your needs. Cheers!

---

