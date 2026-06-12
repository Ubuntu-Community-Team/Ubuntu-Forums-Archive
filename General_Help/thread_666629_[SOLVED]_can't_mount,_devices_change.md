---
title: "[SOLVED] can't mount, devices change"
date: 2008-01-13
forum: General Help
---

### Post by TechnoJunky on 2008-01-13
I've been using Kubuntu since 7.10 was released. I have 3 hard drives, 2 for Windows and 1 for Linux. One of the hard drives for Windows is a data drive that I regularly mount and access. I've written 2 scripts because the device changes. Sometimes it's sdc1 and sometimes it's sdb1 (changes after reboot). I didn't think about this when I decided to use gparted and modify my Linux partition so that I could have a home and a root partition. I went into fstab and modified it so that it would mount /sdb3 to /home. Now sometimes it mounts it and sometimes it doesn't because sometimes it's /sdb3 and sometimes it's /sba3. I've created a new script so that when fstab can't mount it this will, but is there anyway to get K/Ubuntu to permanently call each drive a specific name? Just for the record, the Windows OS drive is an IDE, and the 2 others are SATA.

---

### Post by dgray_from_dc on 2008-01-14
You're talking about static mountpoints.  I have the same problem with USB drives.  I found this [http://ubuntuforums.org/showthread.php?t=91948](http://ubuntuforums.org/showthread.php?t=91948) it didn't help me because there have been changes to how Linux handles hard disks but mainly because I have identical drives.  Maybe this will help you though.

---

### Post by logos34 on 2008-01-14
> **TechnoJunky said:**
> Sometimes it's sdc1 and sometimes it's sdb1 (changes after reboot)... I went into fstab and modified it so that it would mount /sdb3 to /home. Now sometimes it mounts it and sometimes it doesn't because sometimes it's /sdb3 and sometimes it's /sba3. I've created a new script so that when fstab can't mount it this will, but is there anyway to get K/Ubuntu to permanently call each drive a specific name?

Yes, you can use[ ntfslabel]("http://ubuntuforums.org/showthread.php?t=283131") (-->'How to Label').  

Or UUIDs (the default method).

ls -l /dev/disk/by-uuid

blkid

---

### Post by dgray_from_dc on 2008-01-15
> **logos34 said:**
> Yes, you can use[ ntfslabel]("http://ubuntuforums.org/showthread.php?t=283131") (-->'How to Label').  

Or UUIDs (the default method).

ls -l /dev/disk/by-uuid

blkid

Is there a thread on how to use UUIDs?

---

### Post by Keith Hedger on 2008-01-15
To start use:```

sudo mkdir /media/MOUNTNAME
sudo vol_id /dev/DISK 

``` to get the uuid of your disk where DISK is the dev number (/dev/sdb1 for instance) and MOUNTNAME is the name that you want to see the disk mounted as, then use ```
sudo gedit /etc/fstab
``` to open your fstab file for writing then add the line ```
UUID=UUIDFROMVOL_ID /media/MOUNTNAME               ext3    defaults 0       0
```
where UUIDFROMVOL_ID is the uuid you got from vol_id, and presumming you are using an ext3 filesystem on your disk if not you will have to change ext3 above to whatever is appropriate.
save the file and quit gedit
the next time you boot/login your disk will be auto mounted, you can check that youve done everything right by using ```
sudo mount -a
``` which will mount everything according to your fstab.
Hope this helps

---

### Post by TechnoJunky on 2008-01-18
ntfslabel worked great.  I also found from a friend at work that e2label works great for labeling the ext drives (i.e. home).  Thanks for the tip.

---

