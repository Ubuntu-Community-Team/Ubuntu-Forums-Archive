---
title: "$HOME/.dmrc being ignored at log-in"
date: 2007-03-22
forum: General Help
---

### Post by ebsw0820e on 2007-03-22
Upon entering my name and password I'm given this message> "User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users." ...... Then it returns to the log-on screen.

Right now I'm running on the live-CD of my installation (ubuntu 6.06), and attempting the few different solutions I've found by searching online haven't worked. I know I'm either doing something incorrectly or else these solutions can't be executed on live-CD. I'm at a total loss. How do I fix it?

---

### Post by sewmyheadon on 2007-03-22
I just had the same problem and I verified permissions, but I think that the actual problem was that I removed a few partitions and a device and didn't change the fstab file.

[http://www.ubuntuforums.org/showthread.php?t=377283&highlight=fsck.ext3](http://www.ubuntuforums.org/showthread.php?t=377283&highlight=fsck.ext3)

---

