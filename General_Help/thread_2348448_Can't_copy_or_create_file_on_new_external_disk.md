---
title: "Can't copy or create file on new external disk"
date: 2017-01-03
forum: General Help
---

### Post by AUDIOTEK on 2017-01-03
Part of my Linux+ course.   I need to format and partition a disk maintain it, monitor it etc from CLI.

I formated it, created a partition the disk is mounted when I flip to GUI I see it but I cannot move, copy or create files on that drive.



When I try to copy a file (file1.txt) I get this error

Error while copying "file1.txt"

There was an error copying the file into /media/username/c0dfb7.....

The drive is mounted

Device: /dev/sdb1
Partition: Type Linux
Contents:Ext3(version)--Mounted at /media/username/c0dfb7(long string of letters and numbers)

I noticed in their exemple they called the drive newdrive but I can't catch where they inputed the name "newdrive"

When they mount their drive 
sudo mount /dev/sdb1 /mnt/newdrive

They get 
Contents:Ext3(version)--Mounted at /mnt/newdrive


If I do the same command I get;
mount: mount point /mnt/newdrive does not exist

Obviously I haven't created "newdrive" but at one point does newdrive gets created?

---

### Post by Keith_Helms on 2017-01-03
You need to create a folder to use as a mountpoint.  If /mnt/newdrive does not exist, then you'll have to 
```
sudo mkdir /mnt/newdrive
```
You may also want to make yourself the owner of that mountpoint by doing
```
sudo chown myid:myid /mnt/newdrive
```
Then try mounting it and see if you can move files to it.

---

### Post by wildmanne39 on 2017-01-04
> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework servicePlease work out as much as you can and only ask questions when absolutely needed. So far the questions is okay.

---

### Post by AUDIOTEK on 2017-01-04
OK Thanks I will try that.  Very weird that there's no mention of creating a directory to use as a mountpoint.  So that newdrive directory actually lives in root?

---

### Post by AUDIOTEK on 2017-01-04
> **wildmanne39 said:**
> Please work out as much as you can and only ask questions when absolutely needed. So far the questions is okay.  I understand that.  Just sometimes it's frustrating, that online course is OK but I've noticed a few errors mostly with their labs.  It seem that the labs don't connect to their server and it gives you just INCORRECT by default even when you have the right answer, the trick is to reload the lab questions until you get it to connect.  I sent them an email about the issue.   Trust me I do as much research as I can.   I wouldn't want to get a job or a job interview with a certification and have no clue what I'm doing.

Thanks

---

### Post by The Cog on 2017-01-04
> **AUDIOTEK said:**
> OK Thanks I will try that.  Very weird that there's no mention of creating a directory to use as a mountpoint.  So that newdrive directory actually lives in root?

No, it lives in a folder **mnt** which lives in the root. Hence /mnt/newdrive as the folder name. 
/mnt is traditionally a place for putting mount points for drives (I have multiple /mnt/sdax and /mnt/sdbx folders for partitions that I don't normally mount but do occasionally).
/media/username/* is more recent and normally used for automounted removable media like memory sticks, CDs etc.

In case you weren't aware, all drives get mounted somewhere within the existing filesystem structure by replacing a (normally empty) directory with the drive's contents. So there is only ever one filesystem tree, but different branches may reside on different drives.

---

### Post by AUDIOTEK on 2017-01-04
OK so I'm able to mount it under /mnt/newdrive   I had to create that directory.   Now the issue is I don't see that drive in /etc/fstab so I can edit it        I'm starting from scratch the whole process

---

### Post by Keith_Helms on 2017-01-05
> **AUDIOTEK said:**
> OK so I'm able to mount it under /mnt/newdrive   I had to create that directory.   Now the issue is I don't see that drive in /etc/fstab so I can edit it        I'm starting from scratch the whole process

Partitions only get added to /etc/fstab when you first install the system and select mount points for them using the setup screens.  Once your system is installed, you have to manually edit /etc/fstab to add any additional partitions.  Using the mount command does not do it for you.

---

### Post by AUDIOTEK on 2017-01-05
> **Keith_Helms said:**
> You need to create a folder to use as a mountpoint.  If /mnt/newdrive does not exist, then you'll have to 
```
sudo mkdir /mnt/newdrive
```
You may also want to make yourself the owner of that mountpoint by doing
```
sudo chown myid:myid /mnt/newdrive
```
Then try mounting it and see if you can move files to it.


```
sudo chown myid:myid /mnt/newdrive
```

Works.   That part is missing in the course unless it will come later but the instructor is already creating and moving files in newdrive   Is it the only way to create permission on a new partition?

---

### Post by AUDIOTEK on 2017-01-05
> **Keith_Helms said:**
> Partitions only get added to /etc/fstab when you first install the system and select mount points for them using the setup screens.  Once your system is installed, you have to manually edit /etc/fstab to add any additional partitions.  Using the mount command does not do it for you.

I'm trying to modify fstab file with vi.  I need to input this,  now I'm in quota the problem is I don't have the same syntax as what it's on the course.

In vi

I should have the following in the last line of fstab

dev/sdb1 /mnt/newdrive ext3 rw,**usrquota,grpquota** 00

in bold means that's what I need to add

I have something totally different in my fstab file
dev/sdb1 /mnt/newdrive auto nousid,nodev,nofail,x-gvfs-show 00

Should I go ahead and input this?
dev/sdb1 /mnt/newdrive ext3 rw,**usrquota,grpquota** 00

I would usually just do it but I'm on my third day of figuring out that section.  What's the best practice?   Make a backup of the original file just in case I screw it up?

---

### Post by Keith_Helms on 2017-01-05
> **AUDIOTEK said:**
> I'm trying to modify fstab file with vi.  I need to input this,  now I'm in quota the problem is I don't have the same syntax as what it's on the course.

In vi

I should have the following in the last line of fstab

dev/sdb1 /mnt/newdrive ext3 rw,**usrquota,grpquota** 00

in bold means that's what I need to add

I have something totally different in my fstab file
dev/sdb1 /mnt/newdrive auto nousid,nodev,nofail,x-gvfs-show 00

Should I go ahead and input this?
dev/sdb1 /mnt/newdrive ext3 rw,**usrquota,grpquota** 00

I would usually just do it but I'm on my third day of figuring out that section.  What's the best practice?   Make a backup of the original file just in case I screw it up?

Yes, it's always a best practice to make a backup of a system file before you modify it, particularly if you're not very familiar with it.

I had never heard of usrquota and grpquota but I looked them up and they're valid options.  That 00 you're listing should be two fields - 0 0.

I recommend you read over the man pages for fstab and mount.

---

### Post by The Cog on 2017-01-05
You can create a backup of fstab with the command:
```
sudo cp /etc/fstab /etc/fstab-backup
```

If you need to restore the backup (and the system still boots):
```
sudo cp /etc/fstab-backup /etc/fstab
```

---

