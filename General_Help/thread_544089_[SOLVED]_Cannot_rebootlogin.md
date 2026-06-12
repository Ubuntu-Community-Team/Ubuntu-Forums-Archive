---
title: "[SOLVED] Cannot reboot/login"
date: 2007-09-05
forum: General Help
---

### Post by jamesr on 2007-09-05
I am running Xubuntu 6.06 on HP LDpro with 192MB as a intranet  and archival server. It has been running very happily for at least a year but, unhappily, no longer. I noticed the the free space on the boot drive was becoming low >200MB.

I installed SBackup so I could archive the system before activating another drive. I ran the programme, BAD move now I have 3MB of free space and cannot reboot.

The error mentions as a possible source of the problem is lack of space.

I believe that I need a live CD that will boot on this system, then mount the original drive and delete some files. Unfortunately my Gparted live cd does not seem to see the other drive (SCSI) and my older (K)(C)Ubuntu CDs are not live cds or wiil boot properly because of lack of memory. Any suggestions for a live CD that will boot on 192MB system  or any suggestions.

Best Wishes
Jim R.

---

### Post by sumguy231 on 2007-09-05
If you're comfortable with the command line, you should be able to  just reboot into recovery mode and delete things. Barring that, Damn Small Linux is a pretty lightweight LiveCD which you could use to free up space.

---

### Post by jamesr on 2007-09-06
Hi, 
I am very happy with command line approach, but I had tried the recovery mode but the startup asked  for a root password to goto maintenance mode. I entered what I believed was the correct password ie for my main user ie the one asked during administrator tasks and it was incorrect??. That is why I needed another approach.

Thanks about the suggestion about DS Linux I will probably download that. 

I have, in fact , solved the problem by downloading and using TIMOS rescue CD.

Booted to the CD
Checked that I could see the other disk```
#fdisk -l
``` 
Created a directory```
mkdir OLD
```
mounted the old disk```
mount -t ext3 /dev/sdb1 OLD
```
Also tried editting fstab```
nano /etc/fstab
``` and adding a line /dev/sdb1 old ext3  defaults 0 0
then mounting with```
mount -a
``` Both seemed to work
then deleted obvious unnecessary files.```
rm *.html
and so on
```. In the process found that Sbackup was the main culprit, it had filled the space with a file called files.tgz eventhough it was not supposed to be writing to this disk.

Thanks again and as I said, I will take a look at DSL which I believe be loaded onto a USB key

Thanks and Best Wishes
Jim R

---

