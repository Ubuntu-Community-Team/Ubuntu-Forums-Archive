---
title: "New install&gt;chose wrong fs type for ntfs drive"
date: 2016-02-05
forum: General Help
---

### Post by dlanor78 on 2016-02-05
I don't know if I'm just searching wrong or if I did a unique mess up, but I couldn't find another post about this.

I did a new install of Ubuntu, and the way I usually do it is I keep my old home partition (after deleting old config files) and I tell the installer where to mount the ntfs drives I have. I've done this a lot of times so I wasn't paying as much attention as I should have during the install.

On one of the nfts drives, I accidentally chose the ext4 option instead of ntfs. I'm almost positive that I didn't choose to format the drive. I did get a message that popped up but I didn't read it before clicking continue. I know that's not smart, but in the past I've gotten a message during that part that says something about a new size for the drive or partition even if I didn't change the size at all. I thought it was that message unfortunately.

Is there a fairly quick and easy way to set this drive back to ntfs and keep the data intact? The data is mostly steam games which could be downloaded again, but they're huge games that would take a really long time to get again.

Thanks in advance to anyone that can help or just takes the time to try!

---

### Post by sandyd on 2016-02-05
Stop using the disk immediately, the less you write to the disk, the more chance you can recover it.

See [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) for options on how to restore the NTFS partition.

---

### Post by dlanor78 on 2016-02-05
Thanks sandyd!!! 

I chose to use testdisk to fix the partition table and it was surprisingly easy. The link you provided didn't give much info on using testdisk for this, but [http://www.geekyprojects.com/storage/how-to-repair-a-damaged-partition-table-or-mbr/]("http://www.geekyprojects.com/storage/how-to-repair-a-damaged-partition-table-or-mbr/") had great instructions for almost exactly what I needed to do. testdisk still saw the linux part of the partition table as well as the ntfs, so I had testdisk mark the ntfs one as primary. Then wrote the changes to disk and all is well.

I will definitely pay closer attention to what I'm doing in the future even if it's something I've done many times before. All it took was one mis-click and being in a rush to get me into trouble.

---

### Post by dlanor78 on 2016-02-05
Actually, I am still having one problem. Maybe I should start a new thread for it though?

I can't get Ubuntu to see that drive now. Even the live disc. I can manually mount it with ```
sudo mount -t ntfs /dev/sdc1 /media/mountpoint
``` but ```
sudo blkid
``` doesn't show that drive at all.

Testdisk still shows that it thinks there is a ext4 partition on there as well as the ntfs one, so I assume that's the issue. It's getting late so I'll work on it more tomorrow. Any advice is welcome in the mean time though!

---

### Post by oldfred on 2016-02-05
Testdisk seems to always find all the old versions of partitions.

Have you tried chkdsk from Windows on the NTFS partition.
Often after any resize or change, NTFS needs a chkdsk.

---

### Post by dlanor78 on 2016-02-06
> **oldfred said:**
> Testdisk seems to always find all the old versions of partitions.

Have you tried chkdsk from Windows on the NTFS partition.
Often after any resize or change, NTFS needs a chkdsk.

I did try chkdsk and it didn't make Ubuntu see the drive. I did finally get this fixed, or at least it looks like it so far.

When I first used testdisk, it found the ntfs partition and I told it to write the changes to the disk. That only partially worked because Ubuntu couldn't see the drive and Windows saw it, but seemed to crash when trying to write to it. I haven't fully tested to see if it still does this yet.

Here's what I ended up doing (not sure if all steps were necessary). I used gparted to create a partition table on the drive. This make gparted think that the drive was unallocated space. Then I used testdisk to analyze the drive again. It found the ntfs partition and I told it to write it to the disk.

Here is where I did something different from last time. I told testdisk to > Rebuild BS and > Repair MFT. I thinks this is what ultimately did the trick.

I'm in Ubuntu now and the drive shows up fine although I did have to chkdsk in Windows before it would mount. As far as I can tell everything is working as it should. Thanks again for the suggestions and help guys!

---

