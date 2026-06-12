---
title: "Deleted everything on my disks using LVM"
date: 2008-04-10
forum: General Help
---

### Post by Xvani on 2008-04-10
Hi!
I followed [this guide](http://www.debian-administration.org/articles/410) trying to create a single partition with my two disks.

I came to the step where I pvcreated the disks, and then created the volume group.

I then realized that all my data had been deleted. I was not aware of this!

Is there any way to get it all back?

Thanks a bunch!!!

---

### Post by danwood76 on 2008-04-10
I doubt it.
When creating LVM groups you always start from scratch, theres no other way really.

---

### Post by Xvani on 2008-04-10
But the data is still there, it hasn't been overwritten. Surely there must be a way?

---

### Post by cdenley on 2008-04-10
Maybe with testdisk. Did you reformat, or just repartition?

---

### Post by danwood76 on 2008-04-10
if the data is still there then rebuild the partition table manually, or try testdisk, which will normally do the rebuilding for you.

---

### Post by Xvani on 2008-06-10
The data is still there, I can see it using Testdisk, and then "view files".

However, I am not able to rebuild the partition table (or am I? I don't know...)

Testdisk tells me to reboot after writing partition table to disk, but I am not able to mount the fs after rebooting. Am I doing it wrong?

Thanks!

---

### Post by cdenley on 2008-06-10
[http://ubuntuforums.org/showthread.php?t=787798#post4943224](http://ubuntuforums.org/showthread.php?t=787798#post4943224)

The easy way is to use testdisk. If rebuilding your partition table doesn't make your filesystem mountable, maybe some of your filesystem was overwritten. Did you try mounting it with the "mount" command while running a livecd? What error do you get?

---

### Post by greco8523 on 2008-06-20
if the partition is corrupt you may need to use other tools to fix the corruption, TestDisk only detects and rewrites the partition information. This might help you in getting your data back: [http://www.datarecoveryadvice.org/data_recovery_linux_recover_utilities_tools.html](http://www.datarecoveryadvice.org/data_recovery_linux_recover_utilities_tools.html)

What file system is it?

---

### Post by danwood76 on 2008-06-21
You can recover data with testdisk as well partitions.

---

### Post by Xvani on 2008-07-03
A guy at work helped me out. After fiddling around we realized that a bad superblock was the reason we couldn't just use testdisk.

After using testdisk to restore the partitions, we simply ran fsck -y (there were a LOT of errors first time around) and tried mounting again.
This time it worked

Thanks for all your help guiding me in the correct decision

---

