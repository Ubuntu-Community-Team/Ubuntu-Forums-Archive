---
title: "Running out of space - what are my options?"
date: 2006-09-19
forum: General Help
---

### Post by earth_walker on 2006-09-19
Hi everyone.

I originally installed Ubuntu on a spare 4 Gig drive to play with, and have it dual booting windows approximately like this:

hda - 40gig
hda1 - 30 meg fat32 - dell's stupid hidden partition
hda2 - 20 gig fat32 - windows
hda3 - 20 gig fat32 - documents

hdb - 4 gig
hdb1 - 3.6 gig - Ubuntu
hdb5 - about 300 Mb - swap

Of course, it's now a year later and I use my ubuntu for most of my work, with eventual plans to install windows in a vm and repartition the other drive.

HOWEVER, I'm really busy these days, and my ubuntu partition is running out of space: ~600 Mb left, which is fine but requires my attention to keep it from filling up quickly with cache and temp files. 

Are there any options for *quickly* resolving my space issues without any repartitioning? I've cleaned up and uninstalled some stuff, but at this point I'm much more interested in expanding than shrinking.

For example, can I move some of my weightier ~/folders to my fat32 partition and symlink to them or something? Can LVM help me at this point, or only if I had initially set things up with it? 

Should I just maintain until I have to time to do backups, checks, and repartitioning on my other drive to create /home and /usr partitions?

I am not afraid of the cli, but am afraid of spending much time at the moment. Any advice?

Thanks!

---

### Post by aysiu on 2006-09-19
First of all, this command will help free up some space: ```
sudo aptitude clean
``` It deletes all the installer files in /var/cache/apt/archives

> can I move some of my weightier ~/folders to my fat32 partition and symlink to them or something? Can LVM help me at this point, or only if I had initially set things up with it? Yes, you can.

```
sudo mkdir ~/documents
sudo nano -B /etc/fstab
``` If there's a line referring to /dev/hda3, delete it. Then add this line: ```
/dev/hda3 /home/*username*/documents vfat iocharset=utf8,umask=000 0 0
``` Save (Control-X, Y, Enter). ```
sudo mount -a
``` Then copy all your documents to /home/*username*/documents

Replace *username* with your actual username, of course.

---

### Post by earth_walker on 2006-09-19
> **aysiu said:**
> First of all, this command will help free up some space: ```
sudo aptitude clean
``` It deletes all the installer files in /var/cache/apt/archives

 Yes, you can.

```
sudo mkdir ~/documents
sudo nano -B /etc/fstab
``` If there's a line referring to /dev/hda3, delete it. Then add this line: ```
/dev/hda3 /home/*username*/documents vfat iocharset=utf8,umask=000 0 0
``` Save (Control-X, Y, Enter). ```
sudo mount -a
``` Then copy all your documents to /home/*username*/documents

Replace *username* with your actual username, of course.

Thanks for the quick response, aysiu.

I should have clarified that I've already cleaned all temp, cache and apt files, and all my user documents (except, of course, for mail) are already in a separate partition and mounted in /media/documents. My home directory essentially only contains the hidden and desktop directories, so neither of these steps will help.

---

### Post by aysiu on 2006-09-19
Hm. So I'm not sure what you meant by this statement: > For example, can I move some of my weightier ~/folders to my fat32 partition and symlink to them or something? What are your weightier folders?

---

### Post by earth_walker on 2006-09-19
Well, nautilus says that my home folder is 500 megs, most of which are held in: ~/.wine and ~/.evolution. Moving these two would go a long way, if it's possible.

Also, my /usr folder is about 1.5 gigs.

---

### Post by aysiu on 2006-09-19
Hm. Symlinking a config file to FAT32 may not be the best idea, as FAT32 won't support permissions.

Would it be possible to carve out a chunk of the FAT32 partition and format that as Ext3?

---

### Post by earth_walker on 2006-09-19
That would be my 'when I have time' solution, since I'm not willing to resize that partition without doing a full backup first.

---

### Post by aysiu on 2006-09-19
Not sure what else to suggest. You still have 15% of your Ubuntu partition free... that should last you a while unless you're going to be installing a lot of programs.

---

### Post by kick6 on 2006-09-19
do you have double installations of windows software?  As in, do you have things that are installed in windows AND in your .wine folder?

---

### Post by earth_walker on 2006-09-19
> **aysiu said:**
> Not sure what else to suggest. You still have 15% of your Ubuntu partition free... that should last you a while unless you're going to be installing a lot of programs.

You know, that's what I would have thought too. However, there have been several times when I've been doing things concurrently with nautilus, firefox and evolution (e.g. like this morning: converting jpeg files, combining them into a pdf and then attaching that pdf to an email) where the 600 megs of free space 'got used up' (I'm assuming by cache and temp files, since all the actual files I was working with were on another drive) and the system bogged right down windows-style with messages about disk space running out. 

[edit] I love working in ubuntu, but I'm really feeling the restrictions of my initial setup right now, and it's getting in the way of my work. I guess the message here is 'bite the bullet' and put the time in to fix things up.

---

### Post by earth_walker on 2006-09-19
> **kick6 said:**
> do you have double installations of windows software?  As in, do you have things that are installed in windows AND in your .wine folder?

You know, this is a very good point. I am dual booting anyway, so I can afford to get rid of wine for now. It took alot of time to set things up, but I guess I can copy the .wine folder to a backup folder somewhere else until later. I think this is my temporary solution. Thank you, kick6.

---

