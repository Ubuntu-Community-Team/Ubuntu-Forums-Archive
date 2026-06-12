---
title: "Getting Xubuntu to Recognise Windows XP"
date: 2007-04-16
forum: General Help
---

### Post by Andyfield123 on 2007-04-16
I have been using Xubuntu (Dapper) for a while now as a dual boot with Windows XP. How can I get Xubuntu to recognise XP and the files?
Thanks.

---

### Post by Rospo Zoppo on 2007-04-16
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G?highlight=%28ntfs%29]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G?highlight=%28ntfs%29")

---

### Post by Tanoku on 2007-04-16
I don't know what do you mean by "recognise XP" (maybe you want both OSses to be friends? ^^), but accessing the files on your Windows partition from Linux should be pretty straightforward.

Such partition "should" be automatically configured to mount on boot by Ubuntu (or at least it was when I installed). The default mount point is "/dev/sdaX", so I suggest you start by looking on /dev/ if you have any other drives mounted. You may magically find your windows partition there. ;)

If your drive isn't mounted automatically, then do it yourself by installing NTFS read and write support. There's an awesome tutorial on these forums: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by Andyfield123 on 2007-04-16
Thanks works great! :)

---

