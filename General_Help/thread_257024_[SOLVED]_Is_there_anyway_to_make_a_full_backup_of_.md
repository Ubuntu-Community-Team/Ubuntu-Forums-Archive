---
title: "[SOLVED] Is there anyway to make a full backup of Windows, using Ubuntu?"
date: 2006-09-13
forum: General Help
---

### Post by RonB123123 on 2006-09-13
Is there anyway to make a full backup of Windows, using Ubuntu?

My C drive is mounted perfectly on Ubuntu, and I figured since I can get that to work with a simple command, is there a way to make a full backup of windows?

All the backup software we have tried just doesn't seem to work and it would truly be awesome if this is possible.

---

### Post by aysiu on 2006-09-14
PartImage?
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by Shay Stephens on 2006-09-14
You could use partimage or g4l to make an image of the hard drive.  Then you could restore that image at anytime in the future.

aysiu beat me to it ;-)

---

### Post by codejunkie on 2006-09-14
please forgive me for thread highjacking but on dapper when i try and run partimage i get this error 
/dev/dm inode doesn't exists.
Partimage can create it for you.
You can also use the manual mknod
command. Do you want this inode
to be created for you now ?
i've tried choosing yes and now and neither work, this is as far as i get does this have to be run from a live cd or can this be ran straight from the hard drive.

---

### Post by xyz on 2006-09-16
> **codejunkie said:**
> please forgive me for thread highjacking but on dapper when i try and run partimage i get this error 
/dev/dm inode doesn't exists.
Partimage can create it for you.
You can also use the manual mknod
command. Do you want this inode
to be created for you now ?
i've tried choosing yes and now and neither work, this is as far as i get does this have to be run from a live cd or can this be ran straight from the hard drive.

Hi **codejunkie**,
I used **aysiu's** site and it worked flawlessly...except that my backup file (which I put on an external HD) is split in two. The 1st file is 2G and the 2nd about 475MB. I don't know why it won't make 1 single file *and if the fact that it is split in 2 will matter once I need to restore??* I'd feel reassured if someone could give me an answer here. Can't we create a backup file larger than 2G? Other methods allow for a 4G backup file!  :confused: 

About the "inode thing"...I had the same problem! I just hit Enter several times and finally kept my finger on ENTER 'til it went further...and yes I ran it from the LIVE Ubuntu CD.

---

### Post by cssutto on 2006-09-16
I wrote this once and something happened to it, so excuse if it shows up twice.

You can back up with rsync, fast and easy.

Here is my command line:

 sudo rsync --verbose  --progress --stats --compress --recursive --times --perms --links  --exclude=/media/LOCAL\ DISK-1/ --exclude=/media/LOCAL\ DISK/ --exclude=/media/H_\ \ \ \ ~1/ --delete //   /media/LOCAL\ DISK-1/linuxbackupcomplete

/medial/LOCAL\DISK and /media/LOCAL\DISK-1 are names linux gave to my Maxtor external hard drive (two partitions), on which the backup is stored.

You must exclude these because the // tells rsync to back up everything in your system and it will therefore compy the maxtor onto itself.

CSSJR

---

### Post by xyz on 2006-09-17
Also...
I just successfully completed my win backup to an external HD using GParted Boot CD.
It was fast and very easy.
If interested in trying this way:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
**I just forgot one major thing:**
It erased everything that was in there!...live and learn!

---

### Post by oneiota on 2006-11-03
Oh dear!  I have been reading every word here, wishing to make a back up of Windows myself prior to the first leg of my journey from OEM Windows installation to Ubuntu-and-Windows-dual-boot.

If GParted erased everything which you wanted to back up, can you recommend a way to proceed?  I do not wish to erase Windows *yet* but I do wish to back it up prior to partitioning or adding a new drive for a properly installed ubuntu.

---

### Post by aysiu on 2006-11-03
PartImage and GParted are not the same program.

PartImage makes a backup of your partition. GParted deletes, resizes, and creates partitions.

---

### Post by cbalmforth on 2006-11-21
A quick question - is it possible to use partimage to back up the partition you are running it from? I want to run it as a cron job to back up my server at regular intervals.

---

### Post by aysiu on 2006-11-21
> **cbalmforth said:**
> A quick question - is it possible to use partimage to back up the partition you are running it from? I want to run it as a cron job to back up my server at regular intervals.
No.

But if you want to regularly back up your server, you can try using *rsync* instead.

---

### Post by cbalmforth on 2006-11-21
Thanks for the quick reply! 

I know about rsync, as I use it as a cron job to backup the /home directories on my workstations. However I want to make a backup which I can use to quickly and easily restore my server. What directories do I need to backup to do this, and can I just copy them back to an empty partition to restore my server without re-installing Ubuntu? You can't do this with Windows, and it seems far too easy a solution for Linux! Is it really possible to do this or do I need to use something like Partimage or Acronis to backup and restore my  Ubuntu server.

---

### Post by aysiu on 2006-11-21
You can try [this method](http://ubuntuforums.org/showthread.php?t=35087). It's not a script, but you could make it one.

---

### Post by cbalmforth on 2006-11-21
Perfect! It appears that my Windows experiences made me over-complicate a perfectly simple procedure. I can easily modify my rsync workstation backup script to save my server directories.

Thanks pal!

Chris

---

### Post by xyz on 2006-11-22
Thi has already been corrected somewhere on the site but I can't get my hands on the link right now.
If I run it this way, it won't, for instance, exclude "media" under Dapper:
```
tar cvpzf backup.tgz / --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys
```
I need to add / after sys to have it read:
```
tar cvpzf backup.tgz / --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```

---

