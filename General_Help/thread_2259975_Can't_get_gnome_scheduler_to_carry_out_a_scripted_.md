---
title: "Can't get gnome scheduler to carry out a scripted task."
date: 2015-01-08
forum: General Help
---

### Post by Nosphky on 2015-01-08
I installed 'Gnome schedule' to carry out some simple back script tasks but my first attempts at testing fail to get the task completed.  The scheduler does find the script but fails to carry out the backup part - just completes the report saying backup has been completed.

The script works perfectly when run from a terminal and also when run from the file manager.

The part of the script that cron cannot handle is this :

udisksctl mount --block-device /dev/disk/by-uuid/4FED-550C

However, it can handle this part which unmounts the disk :

udisksctl unmount --block-device /dev/disk/by-uuid/4FED-550C

So it appears that the scheduler (cron) has a problem to mount the external drive.  

Can somebody please advise what change I need to make to allow the scheduler to succeed in mounting the drive and making the backup ?

---

### Post by Nosphky on 2015-01-08
I've abandoned gnome-schedule and am proceeding directly with cron.

---

