---
title: "Automatically Backup to a 2nd Internal Drive?"
date: 2007-10-10
forum: General Help
---

### Post by vgrisham on 2007-10-10
Hi,

How do I go about setting up an automated backup of of my Home directory to a second internal hard drive? The second drive automatically mounts when my system boots as /dev/sda1 and is also accessible as /mnt/backup-drive. My home directory has it's own partition at /dev/sdb3.

I'm running Gutsy (gnome). I haven't installed any backup software packages yet.

Ideally, I'd like the backup process to start at around 8:15 A.M everyday and I would like for my computer to shutdown after the backup has completed.

Thanks in advance.
Vaughn

---

### Post by Xenaco on 2007-10-10
See:

[[COLOR="Red"]http://www.mikerubel.org/computers/rsync_snapshots/[/COLOR]]("http://www.mikerubel.org/computers/rsync_snapshots/")

for a tutorial on using **rsync** and **cron** to backup files.

Add the following command after the*** rsync*** command in the **crontab** file:

***sudo shutdown -h +5***

This command will shutdown and powerdown the system in 5 minutes from the issuance of the command.

---

### Post by vgrisham on 2007-10-14
Thanks Xenaco. I appreciate the link and the suggestions. I have settled on pybackpack, and so far, it's working great.

---

### Post by rbmorse on 2007-10-14
Also there  is sbackup from repositories to handle the timed backup part, but you wills till need a chron job for the shutdown.

---

### Post by indytim on 2007-10-15
Or, if you want to have fun and do a bit on the learning curve, you could write a small bash script to copy via compression over to the desired location.  After it's working, then make it an executable and submit it on a cron job.

IndyTim

---

