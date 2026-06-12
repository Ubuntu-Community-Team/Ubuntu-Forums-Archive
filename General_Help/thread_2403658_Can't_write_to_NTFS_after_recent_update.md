---
title: "Can't write to NTFS after recent update"
date: 2018-10-14
forum: General Help
---

### Post by ricardisimo on 2018-10-14
I'm on Xubuntu 18.04. I was writing to my 6TB NTFS drive to my heart's content until some update yesterday (at least I'm assuming that is related... that's the only change as far as I can tell.) All files and folders show up as locked as per permissions, which is not how NTFS is supposed to work, obviously. Sudo (nautilus or thunar) doesn't work either. I can read just fine.

How can I determine what is actually causing the permissions issue and reverse it? Thanks.

---

### Post by yancek on 2018-10-14
Was this an update to your Xubuntu?  Post your /etc/fstab file.  Why do you need an ntfs partition(s) if you are only using Xubuntu?  Check the permissions on the ntfs partition(s) with the ls -l command.

---

### Post by Holger_Gehrke on 2018-10-14
Check whether the file system is mounted read-only by entering ```
 mount|grep '[(,]ro[),]'
```in a terminal. If your drive is in the list this command prints, then it was mounted read-only. Linux does this when it notices problems with a file system. The problem with NTFS is that it's a Microsoft file system and only Windows has tools to check and repair it, so knowledgeable users tend to avoid using it unless it's an external drive and a Windows machine for running chkdsk on the device is at hand.

Holger

---

### Post by ricardisimo on 2018-10-14
I have no idea what happened, but now it is behaving normally. I rebooted twice yesterday, just to see if anything shook loose, but no luck. I guess the third time was the charm. Working fine now.

And I have an NTFS drive because I'm dual-boot. I encode with Adobe programs on Windows, and finish the job on Linux.

Anyhow, thanks to all.

---

