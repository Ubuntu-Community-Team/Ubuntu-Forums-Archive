---
title: "Undoing changes from attempting to enable NTFS write support"
date: 2007-02-24
forum: General Help
---

### Post by HippyVanMan on 2007-02-24
I followed the instructions in the thread ([http://ubuntuforums.org/showthread.php?t=142481&page=1](http://ubuntuforums.org/showthread.php?t=142481&page=1))
And I made a backup of my current settings (bash:~$ sudo cp /etc/fstab /etc/fstab.bak)
I followed the tutorial but it went wrong and now Ive even lost read and write access to a FAT32 drive, and I can no longer see my NTFS drive at all, so I'd like to undo what I did in the tutorial. How?

Thankyou in advance :D

---

### Post by Athropos on 2007-02-24
You just need to restore your backup:

```

sudo cp /etc/fstab.bak /etc/fstab

```

Then after a reboot, everything should be back as before.

---

