---
title: "System boots from wrong drive after DD is used to create an image"
date: 2016-10-18
forum: General Help
---

### Post by Chris_Cooley on 2016-10-18
Hello,

I'm running Ubuntu Server 16.04.1 with three 250GB hard drives.  I've tried to implement software RAID without success and am trying another form of data backup.

The three drives are sda, sdb and sdc.  sda is of course my intended boot drive, and sdb is the backup drive I use DD to write to.  sdb is never mounted (at least not by me).  sdc is just a miscellaneous data drive.  I've created a cron job to run the following command:

dd if=/dev/sda of=/dev/sdb

This works, but when I reboot it boots off of sdb.  I've tried reinstalling GRUB to sda, the issue occurs again after the cron job is ran.  BIOS is set to only boot off of one hard drive, the first hard drive.

Am I missing something here?  Am I not suppose to image a drive like this?

Thank you

---

### Post by sudodus on 2016-10-18
1. You should not clone a drive that is mounted, so do not clone the drive that you booted from. For example, you can boot from a USB live drive, when you clone your main system.

2. If you have two identical drives, the computer cannot tell them apart. Strange unexpected things might happen, when you try to boot from one of them (so after the cloning only one of them should be connected).

3. I prefer Clonezilla to clone a drive or partition and to make a compressed image. It is safer and faster than dd.

-o-

There are better ways to create an automatic backup system - there are several free tools in linux. You can start searching for a tool that works in your case at this link,

[BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by Chris_Cooley on 2016-10-18
Thanks, sudodus...  I guess I was on the wrong track.  What my original idea was is to create an exact duplicate of the boot drive and all its data.  If the boot drive fails, I just swap the SATA cables to boot.

---

### Post by gsahli on 2016-10-18
I'm pretty sure you just have an error in your /etc/fstab. Look at this from mine:
# / was on /dev/sdb1 during installation
UUID=7a90067e-8dd0-4303-945c-98772e1ed821 /               ext4    errors=remount-ro 0       1

The UUID is a unique device ID - that's what remained the same and caused the old drive to boot.Read up on how to generate or find the new drive's UUID and edit fstab to change the reference.

---

### Post by sudodus on 2016-10-19
> **Chris_Cooley said:**
> Thanks, sudodus...  I guess I was on the wrong track.  What my original idea was is to create an exact duplicate of the boot drive and all its data.  If the boot drive fails, I just swap the SATA cables to boot.

Yes, this is possible, and a good way to make 'full backups' maybe twice or four times per year. But the daily (nightly) backup should be made with another tool - just backing up the files that changed since yesterday.

---

### Post by oldfred on 2016-10-19
Some more info on backup.

 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools) 

      
 Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)
Sample rdiff file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)
[http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use)
[https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/)

I just have desktop system. Only a few files, notes & pictures of grandkids are important. And I can reinstall Ubuntu in about 10 minutes. So I just use rsync to copy to another drive (which is not really backup as changed files are overwritten), also most important data is copied to DVD & flash drives.

---

