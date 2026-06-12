---
title: "rdiff-backup-fs"
date: 2018-06-03
forum: General Help
---

### Post by Quarkrad on 2018-06-03
I've started a new thread not to confuse with my other threads on rdiff - looking at rdiff-backup-fs.  **sudo /usr/bin/rdiff-backup --exclude-special-files -v5  /home/dad /media/sf_shared/rdiff** is working fine so I'm looking at rdiff-backup-fs.  My first attempt gave me

```
dad@dad-VirtualBox:~$ rdiff-backup-fs '/home/dad/mnt'  '/media/sf_shared/rdiff' fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
dad@dad-VirtualBox:~$ 
```

Then I read that you can't/not a good idea to have the mount point below /home - so I tried to use the mnt directory in root (rather the mnt directory that sits beside home) and got into a bit of a mess.

---

### Post by wildmanne39 on 2018-06-03
Please do not create duplicate threads and please use this thread.

[https://ubuntuforums.org/showthread.php?t=2393399](https://ubuntuforums.org/showthread.php?t=2393399)

Thread closed!

---

