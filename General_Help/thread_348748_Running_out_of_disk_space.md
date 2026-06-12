---
title: "Running out of disk space"
date: 2007-01-29
forum: General Help
---

### Post by *desk* on 2007-01-29
I have been warned that I am running out of disk space.

My primary drve is 30 Gb which is partitioned to run both XP and Ubuntu.
Is it possible to move all this to a larger drive without losing anything?
Any help would be deeply appreciated

---

### Post by taurus on 2007-01-29
Applications -> Accessories -> Terminal
```
sudo aptitude clean
rm ~/.Trash/*
sudo rm /root/.Trash/*
df -h
```

---

### Post by PointSource on 2007-01-29
If you want to copy/move entire partitions, a program called partimage could be useful.
[http://www.partimage.org/](http://www.partimage.org/)

If you want to stay with your own disk, try getting rid of old data, or resizing the partitions with gparted

---

### Post by *desk* on 2007-01-29
Applications -> Accessories -> Terminal
Code:

sudo aptitude clean rm ~/.Trash/* sudo rm /root/.Trash/* df -h

Taurus, what exactly will the above do?

---

### Post by taurus on 2007-01-29
You need to run each line separately.

```
sudo aptitude clean
```
Will clean out your archives.  

```
rm ~/.Trash/*
```
Will empty your trash can.

```
sudo rm /root/.Trash/*
```
Will empty root's trash can.

```
df -h
```
To check on the space to see how much you have cleaned up.

---

### Post by *desk* on 2007-01-29
Thanks again Taurus
92% is used on hda1 (NTFS)
53% is used on hda6 (ext3)

By the above, it's really XP which is in trouble and I don't want to take any from the linux partition, so my initial question still stands.
PointSource suggested partimage but I don't think it handles NTFS

---

### Post by taurus on 2007-01-29
Yes, ntfs partition is running low, not Ubuntu.  So you still have XP on that partition or is it just a storage?  Maybe you want to boot into XP and start deleting some unwanted/unused programs then.

---

### Post by *desk* on 2007-01-29
I would dispense XP now if I could find software up to the standard of Photoshop SP, Cooledit Pro and Adobe Premiere. And there's other things like my TomTom satnav and my mobile which I would have problems with too.....I think.

---

### Post by Michaelt74 on 2007-01-31
I'm having the same annoying problem. I have a 20gig partition for Ubuntu and currently use about 10 gigs, after using Baobab I see the system currently says I'm using 18 gigs (impossible). I figured the problem must be to do with the backup utility I used. I ran the commands as posted above:

michael@michael-laptop:~$ sudo aptitude clean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
michael@michael-laptop:~$ rm ~/.Trash/*
rm: cannot remove `/home/michael/.Trash/*': No such file or directory
michael@michael-laptop:~$

Is there any way to locate the file that's using up the space?

Thanks! (I'm using Ubuntu 6.10)

---

### Post by Michaelt74 on 2007-01-31
I found a post with a command to find out what's causing the problem
sudo du -sh /*

4.9M    /bin
8.2M    /boot
0       /cdrom
128K    /dev
18M     /etc
7.7G    /home
4.0K    /initrd
0       /initrd.img
109M    /lib
48K     /lost+found
12K     /media
4.0K    /mnt
323M    /opt
898M    /proc
272K    /root
6.3M    /sbin
4.0K    /srv
0       /sys
56K     /tmp
1.8G    /usr
8.2G    /var
0       /vmlinuz

The problem here is the 8.2G /var directory, but I cant '(don't know how) to access it. I can't do it from the desktop as it as I get the following message:
You do not have the permissions necessary to view the contents of "backup".

Strange as I am the only user this computer. So I need to delete the contents in that folder, how do you do this?

Thanks for your help

---

### Post by oracle5 on 2007-01-31
For windows I suggest ccleaner to clear up space and auslogics disk defrag.

[http://www.ccleaner.com/]("http://www.ccleaner.com/")

[http://www.auslogics.com/disk-defrag/]("http://www.auslogics.com/disk-defrag/")

oracle5

---

### Post by taurus on 2007-01-31
> **Michaelt74 said:**
> I found a post with a command to find out what's causing the problem
sudo du -sh /*

4.9M    /bin
8.2M    /boot
0       /cdrom
128K    /dev
18M     /etc
7.7G    /home
4.0K    /initrd
0       /initrd.img
109M    /lib
48K     /lost+found
12K     /media
4.0K    /mnt
323M    /opt
898M    /proc
272K    /root
6.3M    /sbin
4.0K    /srv
0       /sys
56K     /tmp
1.8G    /usr
8.2G    /var
0       /vmlinuz

The problem here is the 8.2G /var directory, but I cant '(don't know how) to access it. I can't do it from the desktop as it as I get the following message:
You do not have the permissions necessary to view the contents of "backup".

Strange as I am the only user this computer. So I need to delete the contents in that folder, how do you do this?

Thanks for your help

Actually, you don't want to delete the whole /var because there are many important subdirectories under it where system logs and others are stored.  Therefore, see which directory is taking up the most space under /var.

```
sudo du -h /var
```

---

### Post by Michaelt74 on 2007-01-31
Thanks Taurus, I ran the command and found the following:

7.9G    /var/backup/2007-01-22_22.11.51.797882.michael-laptop.ful
7.9G    /var/backup
8.2G    /var

Which do I need to delete and what command do I type to delete it?

Thanks, I'm very new at this

---

### Post by taurus on 2007-01-31
Looks like some kind of a backup thing.  To remove it, run

```
sudo rm /var/backup/2007-01-22_22.11.51.797882.michael-laptop.ful
```

---

### Post by Michaelt74 on 2007-02-01
Thanks Taurus, I tried the command but got the following:

michael@michael-laptop:~$ sudo rm /var/backup/2007-01-22_22.11.51.797882.michael-laptop.ful
rm: cannot remove `/var/backup/2007-01-22_22.11.51.797882.michael-laptop.ful': Is a directory
michael@michael-laptop:~$ 

Any suggestions?

Thanks again!

---

### Post by Michaelt74 on 2007-02-01
Problem solved, I found another post detailing the same problem. The command should be

sudo rm -r /var/backup/2007-01-22_22.11.51.797882.michael-laptop.ful

Thanks again for your assistance, I know you guys must get the same questions all day long, but your responses are really appreciated!

[http://www.ubuntuforums.org/showthread.php?t=75339&highlight=remove+directory](http://www.ubuntuforums.org/showthread.php?t=75339&highlight=remove+directory)

---

### Post by maestrobwh1 on 2007-02-14
There are a variety of free disk cloning softwares out there.  I use an old Norton Ghost boot disk I created when I used MS many moons ago.  Aside from fat, fat 32, ntfs, it works with ext2 and ext3 disks and will copy swap partitions also.  It also copies and compresses disk images, as well as clones entire disks or partitions.  You might be able to find someone who has Norton Ghost but then again, you would need a floppy drive.

OR

You can create a bootable Ghost for Linux cd (can you say free?)

[http://freshmeat.net/projects/g4l/?branch_id=48255](http://freshmeat.net/projects/g4l/?branch_id=48255)

I tinkered with it, but it was slower and does not work with USB.  I have one of those USB to ide cables and that is how I like to clone drives that are not part of my desktop system so I don't have to tear it open.  

Ghost for Linux does work otherwise and will either clone or create a compressed image of your drive or partition and i  think it works with most file systems, but it seems you need to know some computer stuff to figure out what options to select (you'll need to select "local" and there is a major emphasis on using the cd with networks but you can use it without being attached to a network) And you'll need to know how the drives are seen in Linux because it is a Linux based program.  

If you have a desktop, set it to boot from cd, then make sure your new drive is connected to an ide interface, and you could make this work... if it is a laptop drive, I guess you would have to connect your old one, make a compressed image of the drive on your desktop machine, then shut down and connect the new drive, reboot with the cd again and "restore" the saved image to the new drive.  Be careful where you save stuff or you could overwrite something you don't want to.

And I think if you have a dual OS and XP is one of them, there is a copy write protection issue and it generally gives you a hassle when you boot and it sees it is on a different drive.  This is one reason why I switched to Linux.  Just one of a few thousand.

---

