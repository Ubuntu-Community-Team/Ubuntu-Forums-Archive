---
title: "Drives dissapeared from /dev, can't boot"
date: 2007-02-27
forum: General Help
---

### Post by Shrodinger on 2007-02-27
I mis-posted this problem under the wrong thread name (turns out it doesn't have to do with console fonts): [http://ubuntuforums.org/showthread.php?t=371538](http://ubuntuforums.org/showthread.php?t=371538), and I don't know how to delete that, but anyway, here is my issue:

My system does not manage when it tries * Mounting local filesystems...

I checked my drive out with a recovery disk, and although there was nothing wrong with the filesystem (from fsck), I don't have my devices where they used to be, before I tried upgrading to feisty.  All of my /dev/hda* are missing, as well as the folder /dev/disk.

How can I recreate these missing devices?  Thanks!

---

### Post by DJ_Peng on 2007-04-10
Due to a drive change in Feisty drives are now as SATA drives. If you haven't gotten this fixed try changing your fstab entries from "hd*" to "sd*".

---

