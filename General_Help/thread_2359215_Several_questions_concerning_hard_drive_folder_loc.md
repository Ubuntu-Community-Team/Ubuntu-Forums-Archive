---
title: "Several questions concerning hard drive folder locations, uuid's, and fstab"
date: 2017-04-21
forum: General Help
---

### Post by cscj01 on 2017-04-21
I am using Ubuntu 16.04.2 x64.

I recently changed the file system on the hard drive I use for user data (labeled Data) from NTFS to ext4.  The NTFS system was there because I had used a dual boot (Ubuntu and XP) for a good while and shared data between them.  Although I had long since stopped using XP, I had not changed out the NTFS file system for an ext4 file system.  The procedure I followed was:

[LIST=1]
[*]copy internal hard drive contents to external hard drive formatted as ext4;
[*](using gpartd for all but the last step) unmount internal hard drive;
[*]delete partition on internal hard drive;
[*]define new ext4 partition on internal hard drive;
[*]remount internal hard drive;
[*]copy data from external hard drive to internal hard drive
[*]
[/LIST]

I was surprised to see that the new mount point for my data hard drive was /media/<username>/Data rather than /media/Data, as it was before.  Additionally, the UUID had changed as well.  This caused me to have to change my FSTAB (I would have had to change it anyway, but I thought the UUID would be the same) as well as numerous programs that were looking for their data to be at /media/Data.

The procedure (or gparted) did not allow me to specify a mount point when I defined the new partition (or at least not explicitly).

Obviously, I am not as up to speed about these issues as I should be.  I would appreciate someone explaining some of the protocol (or calculus) behind the way Ubuntu manages these things.  Your help is greatly appreciated.

---

### Post by Dennis N on 2017-04-21
If you format a partition, it generates a new UUID. **/media/username/xxxx** is Ubuntu's hard-coded mount point for automounting a usb device; also for a partition mounted from the file manager. xxxx will be the label of the partition's file system, if it has one, or its UUID.

To mount a partition somewhere else, you would use the **mount** command to mount manually from the terminal, or make an entry in **/etc/fstab** to mount automatically at startup.

---

### Post by yancek on 2017-04-21
> I was surprised to see that the new mount point for my data hard drive was /media/<username>/Data rather than /media/Data

That changed several versions ago and deleting a partition and creating a new one will generate a new UUID.  You could have simply formatted the ntfs partition to ext4 if I'm reading your post correctly.

---

### Post by cscj01 on 2017-04-21
> **Dennis N said:**
> If you format a partition, it generates a new UUID. **/media/username/xxxx** is Ubuntu's hard-coded mount point for automounting a usb device; also for a partition mounted from the file manager. xxxx will be the label of the partition's file system, if it has one, or its UUID.

To mount a partition somewhere else, you would use the **mount** command to mount manually from the terminal, or make an entry in **/etc/fstab** to mount automatically at startup.

Dennis, you mention that /media/username/xxxx is Ubuntu's hard-coded mount point for automounting a usb device; also for a partition mounted from the file manager.  Are you saying here that using gpartd was mounting from the file manager?  Because I am speaking of an internal hard drive, not a usb device.


> **yancek said:**
> That changed several versions ago and deleting a partition and creating a new one will generate a new UUID.  You could have simply formatted the ntfs partition to ext4 if I'm reading your post correctly.

Thanks for the explanations.  I thought UUID was a property of the disk, so that misconception is corrected.  I seem to recall at some point in the life span of Ubuntu, when defining a partition, one was asked for the mount point.  yancek has confirmed that.  So had I just reformatted the NTFS partition to ext4, things would have been much simpler; only changing the definition in FSTAB.

With that said, there are still application that depend on my data disk being at /media/Data.  Would you folks suggest I change the mount point of Data back to its original location.  So far, I have only changed a couple of programs.

Thanks for your explanations.  One can always learn.

---

### Post by Dennis N on 2017-04-22
By "partition mounted from the file manager" I meant you mount one of the devices (partitions) listed on the side pane (see attachment) from this window. I always give them all labels for easy identification. In the picture, Korora is selected and mounted (by either enter or double-click). It mounts at /media/dmn/Korora; the label Korora becomes the name of the root folder. The point is, all these devices mounted from the side pane always mount under /media/dmn (for me, that is).

---

### Post by cscj01 on 2017-04-22
Okay, after learning some valuable facts from my two helpful repliers, I changed FSTAB to reflect the old mount point, /media/Data, changed Disks>Mount Options to reflect this, and rebooted.  I then changed the two applications to look for their data in the old location.  After testing, all is well.  So I do not need to worry about all the other applications.

Thanks again for your help Dennis N and yancek.  With that, I'll mark this thread as "Solved."

---

