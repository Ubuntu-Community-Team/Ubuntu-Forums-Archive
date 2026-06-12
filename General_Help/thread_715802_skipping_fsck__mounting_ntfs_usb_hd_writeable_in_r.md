---
title: "skipping fsck / mounting ntfs usb hd writeable in recovery shell"
date: 2008-03-05
forum: General Help
---

### Post by scicode on 2008-03-05
I dropped my laptop and made some damage on the hd, however starting ubuntu still worked (with a couple of wait times when the damaged sectors were tyed to access).
So I wanted to make a backup and got a usb hd (ntfs) from my buddy. On booting ubuntu again however fsck started and required a scan. The scan failed due to the hd errors and a recovery shell opened where the fs is mounted in read only. Since I can still copy data from the hd i though i just mount the usb hd and copy everything i need onto the usb hd. However the auto-mount failed and a manual mount also failed with the error fuse: failed to create temporary directory (no wonder the fs is mounted read only).
Can I somehow prevent fsck from starting?
I do not want to run a fsck manually since there are too many errors and I do not want to overwrite data. Can I run fsck manually without it doing anything?
Recovery mode also starts fsck.
My laptop has no optical drives so i have no chance of running a live cd. Anything that has to do with going into the internet was broken since the acciedent. Some files that enable internet connections seem to be in damaged sectors.

Any suggestions what I can do now? Please help.

**Edit**
I was able to start my backup by remounting the filesystem with write access 
```
mount -n -o remount,rw /
```

---

