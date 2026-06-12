---
title: "[SOLVED] Using Tar to backup system"
date: 2007-09-20
forum: General Help
---

### Post by tech9 on 2007-09-20
:KSHeliode:KS had a great backup solution with these commands

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

tar xvpfz backup.tgz -C /

The only problem with this is that if you completely delete your partitions and create new ones the UUID do not match and your system errors on boot up.

Can someone confirm that the UUID are located in /etc/fstab?

If this is the case, I could exclude the fstab file and backup everthing else... and I would be able to restore my backup tar file to any new partition.:)

Please Advise,

Thanks

---

### Post by psusi on 2007-09-20
Yes, the UUID is referenced in /etc/fstab.  You could just update the UUID after a restore, or change from UUID to the device name and just recreate the same number of partitions, in the same order.  

I set up my server at work to back up every night with a cron job to run tar.  You can name the file `date +%F`-full-backup.tgz and you get a nightly backup with that day's date in the name.  I do a full backup once a week, then a nightly incremental backup using the -g option.  

You also might switch the -z to -j to get better compression with bzip2, at increased cpu cost.

---

### Post by tech9 on 2007-09-20
> **psusi said:**
> Yes, the UUID is referenced in /etc/fstab.  You could just update the UUID after a restore, or change from UUID to the device name and just recreate the same number of partitions, in the same order.  

I set up my server at work to back up every night with a cron job to run tar.  You can name the file `date +%F`-full-backup.tgz and you get a nightly backup with that day's date in the name.  I do a full backup once a week, then a nightly incremental backup using the -g option.  

You also might switch the -z to -j to get better compression with bzip2, at increased cpu cost.


Thanks psusi!
I will try this:)

Also thanks for being the only one to respond out of 21 people.:mad:

.......

I have solved this issue....

[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)

---

