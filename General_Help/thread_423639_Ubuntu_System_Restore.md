---
title: "Ubuntu System Restore"
date: 2007-04-26
forum: General Help
---

### Post by deylo on 2007-04-26
hey guys, i have just installed ubuntu 7.04 (for the 100th time) and i was wondering if there is anyway i can save its current state (something like Windows Xp System Restore). i want to be able to 'rollback' to a previous restore point just in case i mess up anything because i am new to linux and i like digging around in it so i know sumtime i must mess up something....:P

---

### Post by spankymasterc on 2007-04-26
Thats what im looking for to hope someone replies with something like it because right now i have it perfect... even though ive only installed once with no problems i want to keep it that way....

---

### Post by spankymasterc on 2007-04-26
Hey dude i looked around, instead i found this and it seems pretty useful backup when ever u want and what ever you want and then easily retore it.....

[http://onlyubuntu.blogspot.com/2007/03/backup-and-restore-ubuntu-system-using.html](http://onlyubuntu.blogspot.com/2007/03/backup-and-restore-ubuntu-system-using.html)
try it man i am about to do it :D 

::cheers::

---

### Post by mpooley on 2007-04-26
Do you know what folders or files you need to  back up if you are doing a complete re-install but want to keep all your settings?

---

### Post by musther on 2007-04-26
My solution to this relies on having / (your root partition) separate from /home (your home partition).  If you only have one partition this wont work, but if you have two in this config, then it will.

Download the system rescue CD:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

and burn it to a CD, put it in your CD drive, reboot.

When the rescue CD has booted, mount your /home partition and then load the program partimage.  Partimage will let you back up your / (root) partition to a file on your home partition.  If you ever need to you can restore the image.

So, if your partitions are like this:
/dev/hda1 - linux swap
/dev/hda2 - /
/dev/hda3 - /home

Then, after booting the CD do:

```

mkdir /mnt/home
mount /dev/hda3 /mnt/home
partimage

```

Then you choose to backup /dev/hda2 and choose to save the backup as something like:
```
/mnt/home/backup
```

Hope that's helpful.

---

### Post by deylo on 2007-04-26
spankymasterc im gonna check out that site u suggested.
musther, mpooley those suggestions yall gave wouldn't they have to use extra disk space in that i would have to actually save an image of my files/folders? i was kinda lookin for jus having a simple resotre point where i can go back if anything goes wrong and would not take up alot of disk space

---

### Post by spankymasterc on 2007-04-26
actually no i dont know what folders to do a complete backup but ill look around any help would be appreciated to :D 

::Cheers::

---

### Post by lakersforce on 2007-04-26
> **musther said:**
> My solution to this relies on having / (your root partition) separate from /home (your home partition).  If you only have one partition this wont work, but if you have two in this config, then it will.

Download the system rescue CD:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

and burn it to a CD, put it in your CD drive, reboot.

When the rescue CD has booted, mount your /home partition and then load the program partimage.  Partimage will let you back up your / (root) partition to a file on your home partition.  If you ever need to you can restore the image.

So, if your partitions are like this:
/dev/hda1 - linux swap
/dev/hda2 - /
/dev/hda3 - /home

Then, after booting the CD do:

```

mkdir /mnt/home
mount /dev/hda3 /mnt/home
partimage

```

Then you choose to backup /dev/hda2 and choose to save the backup as something like:
```
/mnt/home/backup
```

Hope that's helpful.

Dont get me wrong, but this is why I actually sometimes like Windows. There you just press the "restore" button :lolflag:

---

### Post by musther on 2007-04-26
Any method of backup will use disk space.  In windows, the restore point is just a backup of all files (but it only backs up those that change since the restore).  This is quite a clever way to use less disk space, but as yet I don't think any feature like this exists for linux. The image created with partimage is compressed though, and your / is unlikely to be larger than 4gb unless you have a lot of stuff installed.

It would be a good feature for ubuntu to have a restore system.

---

### Post by Ric95 on 2007-04-28
Srestore works well, but only if you can get back to the graphic interface. If X is screwed you'll still need to do the reconfigure thing and get back to a basic driver to restore.

---

### Post by musther on 2007-04-29
Srestore is really Sbackup apparently, anyway the homepage is:
[http://sbackup.sourceforge.net/HomePage](http://sbackup.sourceforge.net/HomePage)

It's in the repos.

---

### Post by deylo on 2007-04-30
ok guys thanx!!

---

