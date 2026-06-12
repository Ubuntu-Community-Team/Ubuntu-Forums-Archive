---
title: "Using davfs2 with Cubby.com"
date: 2014-02-09
forum: General Help
---

### Post by algonquinn on 2014-02-09
Hello,

I am attempting to use Cubby.com to create a cloud backup of my entire Documents folder. My plan is to use Cubby to keep things synchronized across my multiple machines with rsync. I was wondering if anybody has had much success getting Cubby working in Linux.

The approach I have seen so far is to mount your folder using WebDAV via davfs2. So far, I have done the following:

1) Added the line "use_locks 0" to /etc/davfs2/davfs2.conf
2) Mounted the cubby filesystem with: sudo mount.davfs [https://webdav.cubby.com](https://webdav.cubby.com) ~/cubby -o rw
However, I am now having the "filenames with spaces" issue. This was described previously (link below) and I was wondering if anyone has found a workaround. I need spaces since I am syncing my Documents folder, and I don't want to mass-rename all of my document files.

Link to prior post: [http://ubuntuforums.org/showthread.php?t=2130743&p=12580724#post12580724](http://ubuntuforums.org/showthread.php?t=2130743&p=12580724#post12580724)

Thanks!

---

