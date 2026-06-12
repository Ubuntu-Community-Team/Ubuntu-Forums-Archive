---
title: "best way to backup?"
date: 2007-01-09
forum: General Help
---

### Post by insert_name_here on 2007-01-09
What would be the best way to back up a 6.10 system to an external hard drive, hopefully to some sort of image file?  Ideally, this solution would also be able to back up my windows xp partitions, but that isn't necessary.  

btw, I used to use norton ghost, but that has decided to not work anymore.

thanks for hte help

---

### Post by llamakc on 2007-01-09
What all do you want to back up? Just /home?

---

### Post by rioghal on 2007-01-09
I use PartImage to make a disk image of the entire install. I do that once per week and I have had to restore from those images a time or two. What it does is take your entire install, copy it, compress it (user configurable) and you can burn that image to a DVD or leave it on a hd. I found that the restored image was the same way I left it.. it's sort of like Norton Ghost for Linux.

PartImage can be found here:
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

And is also included on the System Rescue CD, found here:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

I recommend everyone have a copy of sysresccd.

EDIT:
It seems that the System Rescue CD now has a window manager, WindowMaker, and updated versions of most of the apps. I'll have to download the new version :)

---

### Post by aysiu on 2007-01-09
You may also want to look into [*ddrescue* ](http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html) or [*tar*.](http://ubuntuforums.org/showthread.php?t=81311&amp;highlight=howto+back+up+restore)

---

### Post by tc101 on 2007-01-11
How about using Simple Backup?  In another thread lots of people seemed to think that was the best thing to use.

Also, how about some kind of offsite backup?  Is the best thing just to zip up your backup file and FTP it to some site where you have storage, or is there a better way?

I don't know anything about any of this.  I am new.  I am just asking?

---

### Post by Moldz on 2007-01-11
Well you could FTP it to some server on a distant land but, I would recommend you do something more secure.

You should probably SCP or SFTP it.  Also, make sure you trust the server since all your files might be freely available for a curious admin to poke through.  You might want to encrypt it in that case.

---

### Post by tc101 on 2007-01-11
So how would you do an off site backup?  I think it is a good idea to do one.  Think about what would happen if my house burned down.  If my data was just burned on CDs sitting in my office with my computer I would still lose everything.

One simple solution is just to put the CD in the glove compartment of my car, but it would be easier to do something on line if it could be secure.

---

### Post by tc101 on 2007-01-13
Yesterday I backed up /home by right clicking on it in Nautilus and doing a "create archive" which made a file ending in .tar.gz, which is a tar archive (gzip-compressed).  I then copied this to a CD.  Is this a safe way to backup?  What would I be missing by doing this?  What would I gain by using some backup software like Simple Backup?

I am just learning ubuntu.   There is nothing very important in my install right now.  If I lost everything and had to start from scratch it would not be a great disaster, but I just want to understand how all this works.

---

### Post by ardchoille42 on 2007-01-13
> **tc101 said:**
> Yesterday I backed up /home by right clicking on it in Nautilus and doing a "create archive" which made a file ending in .tar.gz, which is a tar archive (gzip-compressed).  I then copied this to a CD.  Is this a safe way to backup?  What would I be missing by doing this?  What would I gain by using some backup software like Simple Backup?

I am just learning ubuntu.   There is nothing very important in my install right now.  If I lost everything and had to start from scratch it would not be a great disaster, but I just want to understand how all this works.

That's basically what I have been doing for over two years (except I use a bash script to do the same thing) and it works for me. That is a simple way to backup your home directory without having to install and learn a new app and I don't think it would miss anything since it backs up everything in $HOME. I have had to restore my system a few times from this kind of backup and it always yields the same files as I had when the backup was done. I feel this is the best way to backup your $HOME.

Here is the script I use to do this:

```

#!/bin/bash
#
# This script makes a backup of /home/USERNAME
# You can run this script from a daily cronjob with:
# 00 04 * * * sh /path/to/this_script
# The above would run this script at 4 every morning
# You can remove the below parts you don't want to do

# Change directory to /home/USERNAME - REQUIRED!
cd /home/USERNAME

# Empty the trash - Optional
if [ -e /home/USERNAME/.Trash/* ]
then
    rm -r /home/USERNAME/.Trash/*
fi

# Delete thumbnails - Optional
# you can prevent nautilus from creating a ~/.thumbnails
# directory by running this command in $HOME: ln -s /dev/null .thumbnails
if [ -d /home/USERNAME/.thumbnails ]
then
    rm -r /home/USERNAME/.thumbnails
fi

# Clear the recently used list - Optional
# you can prevent nautilus from creating a .recently-used
# file by running this command in $HOME: ln -s /dev/null .recently-used
if [ -e /home/USERNAME/.recently-used ]
then
    rm /home/USERNAME/.recently-used
fi

# Delete the xsession errors file - Optional
if [ -e /home/USERNAME/.xsession-errors ]
then
    rm /home/USERNAME/.xsession-errors
fi

# Clear the gedit search list - Optional
if [ -e /home/USERNAME/.gconf/apps/gnome-settings/gedit/%gconf.xml ]
then
    rm /home/USERNAME/.gconf/apps/gnome-settings/gedit/%gconf.xml
fi

# Clear bash history - Optional
echo "" > /home/USERNAME/.bash_history

# Backup personal files - REQUIRED!
# Change pwd to /home
cd /home

# Tar up all files in /home/USERNAME - REQUIRED!
tar cjf /path/to/backups/temp.tar.bz2 USERNAME

# Change the path of the tarball - REQUIRED!
if [ -e /path/to/backups/$(date +%Y%m%d)-backups.tar.bz2 ]
then
    rm /path/to/backups/$(date +%Y%m%d)-backups.tar.bz2
fi
mv /path/to/backups/temp.tar.bz2 /path/to/backups/$(date +%Y%m%d)-backups.tar.bz2

# Done
exit


```

You'll need to change "USERNAME" to your user name and create (make the directory) the path where you want to save the backup (I used /mnt/hdb1/backups). This script will save your $HOME to a b-zipped tarball with the date in the filename:

```

[~ @ 11:51:40] ls -la /mnt/hdb1/backups/
-rwxr-x--- 1 USERNAME USERNAME 4868151 2007-01-09 11:12 20070109-backups.tar.bz2
-rwxr-x--- 1 USERNAME USERNAME 4890293 2007-01-10 07:08 20070110-backups.tar.bz2
-rwxr-x--- 1 USERNAME USERNAME 5436623 2007-01-11 04:00 20070111-backups.tar.bz2
-rwxr-x--- 1 USERNAME USERNAME 5489094 2007-01-12 04:00 20070112-backups.tar.bz2
-rwxr-x--- 1 USERNAME USERNAME 5577305 2007-01-13 04:00 20070113-backups.tar.bz2

```

This will allow you to do daily backups without having to do any work: you can put the script in a daily cronjob and let it run. Then, oh.. say.. once per week, you can burn the /path/to/backups (or whatever you specified) dir to a cd/dvd in case you need it later.

I hope this helps.

---

### Post by shane2peru on 2007-02-01
Ok, I want to take this post a step further.  There are few posts out there about the best way to backup.  What I want to know is about backing up not just my /home, but backing up everything automatically.  I have not had to restore too much but on occasion I have had to restore.  I'm currently using the tar method with a crontab for the system.

```
###My Backup Script
/bin/tar cpjf /mnt/data/Backups/fullbackup`date +%Y-%m-%d`.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/media --exclude=/mnt --exclude=/home/USERNAME/Pictures --exclude=/sys / > /home/USERNAME/log/tar_cron`date +%Y-%m-%d` 2>&1

```  
Here is my current script.  Is there a better automated way to do this other than tar?  I guess that is my real question.  Thanks.  

Shane

---

