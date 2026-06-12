---
title: "Missing tons of storage space"
date: 2023-11-29
forum: General Help
---

### Post by Medieval Cow on 2023-11-29
Hi all, I've got Xubuntu installed on a partition with ~670 GB of space. Checking Disk Usage Analyzer, Disks, or just the "df" command in Terminal shows almost all of that space being taken up (only 37 GB free), when the disk usage should be much, much lower. Running an actual scan on the partition with Disk Usage Analyzer only comes up with 163 GB used, which is much more in line with the usage I'd expect. This is also the amount of usage I get if I just go to / in File Manager, select every folder (except Proc) and get their properties.

I've tried forcing fsck to run, but that didn't resolve the issue. I just recently set up BackInTime to run backups of my machine and initially seem to have misconfigured it so it wasn't backing up properly to my external hard drive. I've since resolved that, but I'm wondering if there's some weird shadow backups hiding on my machine somewhere?? I have no idea why I wouldn't be able to see them anywhere though, so maybe that's a red herring.

I'm tearing my hair out trying to figure out why the heck it thinks all my space is taken up when it actually isn't. I've been banging my head against the wall for a couple days on this and I'm just spinning my wheels, so I'm hoping someone can point me in the right direction to figure out what on Earth is going on. Thanks!

---

### Post by yancek on 2023-11-29
You might run a search using the find command with various options and locations.  The link below has some simple examples and you can set the size to whatever you want.  Look for files/directories which may have been created by your BackinTime software as they may have been written to the drive.  I would expect you would be able to see them but I've never used it so don't know.

[https://ostechnix.com/find-files-bigger-smaller-x-size-linux/](https://ostechnix.com/find-files-bigger-smaller-x-size-linux/)

Check /var/log and check for hidden files, reboot.

---

### Post by Rubi1200 on 2023-11-29
What does this show?
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```

Have you tried removing older kernels to free up space?
```
dpkg --list | grep linux-image

```

---

### Post by MAFoElffen on 2023-11-29
I would also like to see this:
```

du -h / 2>/dev/null | grep '^[0-9]*\.[0-9]G'

```

---

### Post by TheFu on 2023-11-30
Having a big disk doesn't mean there are partitions or file systems on it.
In addition to the other requested commands, 
```
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
```
wrapped in code-tags would be useful.

---

### Post by MAFoElffen on 2023-11-30
+1 -- Very true. I normally do not partition all my space to max. I reserve for future growth & emergencies.

---

### Post by ian-weisser on 2023-11-30
> **Medieval Cow said:**
> I just recently set up BackInTime to run backups of my machine and initially seem to have misconfigured it so it wasn't backing up properly to my external hard drive. I've since resolved that, but I'm wondering if there's some weird shadow backups hiding on my machine somewhere?? I have no idea why I wouldn't be able to see them anywhere though, so maybe that's a red herring.

On the other hand, that might be exactly the problem.

Yes, it's possible to hide data "underneath" a mount point. Hidden and inaccessible when the device is mounted.
Try unmounting your BackInTime device(s), and see if that mount point suddenly becomes a local directory full of gigs of old backups.

---

### Post by TheFu on 2023-11-30
> **ian-weisser said:**
> On the other hand, that might be exactly the problem.

Yes, it's possible to hide data "underneath" a mount point. Hidden and inaccessible when the device is mounted.
Try unmounting your BackInTime device(s), and see if that mount point suddenly becomes a local directory full of gigs of old backups.

This is a common issue when folks try to mount storage for backups, but it doesn't work all the time, perfectly, and they don't have validation checks to prevent backups from running if the storage isn't actually mounted.  I know it has happened to me.  

There are 2 popular methods to validate that backup storage is actually mounted.

a) check the mount table and verify that the specific location has extra storage mounted to it.  It is basically a **mount |grep -c  ** command in an 'if - fi' check.

b) Create a specific file in the directory where the extra storage will be mounted.  Something like ".not-mounted" - then check if that file exists. If it does, then the backup storage isn't mounted. If it does not exist, then the backup storage is mounted and all is well to continue.

Simple checks, if you know to do them.  Of course, once you add one of these extra checks, the issue will never happen again. ;)

---

### Post by ian-weisser on 2023-11-30
> **TheFu said:**
> b) Create a specific file in the directory where the extra storage will be mounted.  Something like ".not-mounted" - then check if that file exists. If it does, then the backup storage isn't mounted. If it does not exist, then the backup storage is mounted and all is well to continue.

Simple, yet clever. Brilliant.

---

### Post by Medieval Cow on 2023-12-01
> **ian-weisser said:**
> On the other hand, that might be exactly the problem.

Yes, it's possible to hide data "underneath" a mount point. Hidden and inaccessible when the device is mounted.
Try unmounting your BackInTime device(s), and see if that mount point suddenly becomes a local directory full of gigs of old backups.

Ah, this was it! Somehow the drive must have gotten unmounted and it did indeed just fill up the whole hard drive "backing up" locally instead of to the external drive. Unmounted, cleared that unfinished partial backup out, and now I've got all my space back.

Thanks so much for all the quick replies, this really had my sanity teetering on the brink!

---

### Post by TheFu on 2023-12-01
> **Medieval Cow said:**
> Ah, this was it! Somehow the drive must have gotten unmounted and it did indeed just fill up the whole hard drive "backing up" locally instead of to the external drive. Unmounted, cleared that unfinished partial backup out, and now I've got all my space back.

Thanks so much for all the quick replies, this really had my sanity teetering on the brink!

We've all had the same issue. That's why we know it so well.  

Be certain you add some code to your backup script that validates the backup storage is actually mounted, so this can never happen again.  I'd post some sample code, but I switched to using "pulled" backups from a different system years ago and my backup storage is mounted via **autofs**. 

In short, not being mounted doesn't happen anymore here and if there is a failure, it fails very loudly.  I prefer failures to be loud and when things are working as planned, for that to be silent. Success should be silent.   crontab has a method for good messages to be ignored and errors to be emailed, as an example. Excellent design.

---

### Post by Medieval Cow on 2023-12-02
Agreed! I'm not running a script, I'm using the program Back In Time, so it's not as easy to add a check there when it backs up specifically. Honestly, it already kind of fails loudly though, because I'm backing up my Home folder and also an external drive with tons of media on it (this is a media center PC), so a single backup attempt will immediately fill the whole hard drive and make things get wonky. Loud failure accomplished! Maybe I'll set up a cron job to check to see if it's mounted a few times a day and notify me if it gets unmounted somehow though, so I can at least jump on top of it ASAP instead of waiting for things to start breaking. Thanks for the advice!

---

### Post by TheFu on 2023-12-02
Back In Time has lots of default stuff in the way it works.  It is really not designed for backing up media. It is for single-user systems with 1 HOME directory and typical settings and documents.  Also, Back In Time runs hourly to create a new set of backup versions using hardlinks on the target storage.  Over time, those hourly copies are selectively removed over time.  

It is slick, provided you understand the limitations.

For media files, I use a daily **rsync** script and only have 1 copy.  I just can't afford to have versioning of media file backups.  After all, they don't change besides having files added and removed. Versioning isn't useful and just means a file is corrupted (which can happen).
My media backups are basically this for each file system:
```
ionice $rsync -ar --stats --info=progress2 $EXCLUDES --delete-during       /d/D1/      /d/b-D1/
```

Before the lines like that, I clean up the different Trash directories to prevent those from becoming huge if I forget to disable using Trash in the GUI/File manager.
Because the media mirrors are inside the same computer, no compression is used (that's the -z option, typically  -avz).

For media files, the owner, group, ACLs, permissions and xattrs aren't so important.  If I need to restore them, I'll run a few chown/chgrp/chmod commands recursively to set the file permissions as needed for my media server software.  However, for all other files, getting exactly the correct, current, owner, group, permissions, ACLs and xattrs is very important.  Those can change over time, which is why hardlink-based backup tools like back-in-time aren't the best.  They only keep the most recent file metadata, not versioned.

---

