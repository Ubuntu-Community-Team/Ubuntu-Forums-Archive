---
title: "What is my drive status? Not a problem, a condition!"
date: 2014-10-03
forum: General Help
---

### Post by Kurt_Alan on 2014-10-03
If I want to drag/drop a file to my flash drive on my desktop, or to copy/paste to it, the latter is greyed out and the former will not accept the drag/drop.

However, from CLI I can sudo cp a data file to the drive without issues.

Why can I do one and not the other? How would I characterize this drive's status?

Is this a chown config issue?

---

### Post by Impavidus on 2014-10-04
When you drag and drop or when you copy and paste you don't use root permissions. When you use sudo cp, you use root permissions. So the question is why you need root permissions. What do you get from```
mount
ls -ld /path/to/flashdrive
```

---

### Post by Kurt_Alan on 2014-10-04
****

Meanwhile, before I read your reply I tried ```
 lsblk -m 
``` and the result is ```
      &#9472;sdb1   7.3G root  disk  brw-rw----
    
```

It seems that the problem is that the owner is root and not user.  If it was user with rwx permissions, I could do everything. I'm not sure whether the problem is permissions or owner or both?

Probably irrelevant but the drive is formatted ext4.  Also, I cannot download to drive from cloud because of error message "permissions not accepted."

For Linux, then, what should be my standard procedure when I insert a drive and want full functionality rather than like now where I am limited to root?

---

### Post by tgalati4 on 2014-10-04
So the flash drive (let's assume it is an SD card for this example) has root permissions.  You can do a few things:

Make a directory.  Assume that the drive is called /mnt/alank/1234-1234

```
sudo mkdir /media/alank/1234-1234/My_Backups
```

Now take ownership:

```
sudo chown -R alank:alank /media/alank/1234-1234/My_Backups
```

You should now be able to drag and drop files to the card using Nautilus.  Remember to "Eject" or "Unmount" the SD card before pulling it out of the computer.  Failure to do that will result in an "unclean" file system which forces it to be read-only.  You will need to "clean" it using *fsck*.

---

### Post by Kurt_Alan on 2014-10-04
> **tgalati4 said:**
> So the flash drive (let's assume it is an SD card for this example) has root permissions.  You can do a few things:

Make a directory.  Assume that the drive is called /mnt/alank/1234-1234

```
sudo mkdir /media/alank/1234-1234/My_Backups
```

Now take ownership:

```
sudo chown -R alank:alank /media/alank/1234-1234/My_Backups
```



Your solution worked but not exactly in the way you described it. Does this make sense?
1. With the drive NOT plugged in, if I go to Thunar File Manager I have /media file empty.
2. When I DO plug in the drive, I now get /media/lucas/b0ff_name_of_drive.  The system automatically creates my user folder "lucas" and then places the drive inside of that.

Therefore, I skipped the mkdir step.  After inserting the drive I did one thing: ```
 sudo chown _R lucas:lucas /media/lucas/b0ff_name_of_drive 
``` and then I had full user permissions, could download to the drive, copy/paste to it, etc.

I had to do same with each of my external (flash) drives--but one time only. 
1. Does what I did make sense?
2. The fact that I had to chown for every drive, would you call this a Linux quirk or would you call this a "Linux is not Windows" situation?

---

### Post by Kurt_Alan on 2014-10-04
erratum:  chown -R

---

### Post by yancek on 2014-10-05
> The fact that I had to chown for every drive, would you call this a  Linux quirk or would you call this a "Linux is not Windows" situation? 		

The command you posted changed the owner:group and permissions on that specific flash drive.  I don't know why you would expect it to change permissions on another flash drive that wasn't attached to the computer.  Check the permissions on /media and /media/alank.

---

