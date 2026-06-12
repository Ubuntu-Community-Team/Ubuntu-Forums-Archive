---
title: "Scan Disk For Errors HowTo"
date: 2007-04-28
forum: General Help
---

### Post by nami on 2007-04-28
I seem to have errors on my partition.  In Windows XP, there is a function which lets you do a disk check which scans and fixes any problems/errors.

How can I do this in Ubuntu 6.10?

---

### Post by mdurham on 2007-04-28
> **nami said:**
> I seem to have errors on my partition.  In Windows XP, there is a function which lets you do a disk check which scans and fixes any problems/errors.

How can I do this in Ubuntu 6.10?

I think you have to use 'fsck' (as root, with drive unmounted). I suggest reading the man page as there are several options.

---

### Post by cafonso.ca on 2007-07-25
A safe way is to use tune2fs to reconfigure the behavior of fsck at boot. Like:

 sudo tune2fs -c 20 /dev/sda1

would make fsck to run automatically on /dev/sda1 every 20 boots, and

 sudo tune2fs -c 1 /dev/sda1

would make it run *every* time you boot on /dev/sda1

If your disk is eternal, you can disable running fsck at boot altogether with:

 sudo tune2fs -c 0 /dev/sda1

but your disk is not eternal, of course :)

More info in:

[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)


--c.a.

---

