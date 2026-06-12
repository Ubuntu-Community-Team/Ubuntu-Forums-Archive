---
title: "[SOLVED] Can't access NTFS partition anymore."
date: 2008-07-04
forum: General Help
---

### Post by dodle on 2008-07-04
My ntfs partition, which has all my important files, used to mount automatically upon starting ubuntu.  Now if I try to mount it, I'm given an error saying that Windows did not shut down properly.  I've tried restarting and shutting down Windows several times with the same result.

I have two ntfs partitions, one with WindowsXP, and one for keeping all my files.  Next time I'll use a Linux partition for storing my stuff.  

Ext2fsd is a neat tool that has worked flawlessly for me to access my Linux partitions from Windows.

---

### Post by dodle on 2008-07-05
Okay, I know for sure now that the problem is on Windows' end.  I can't shut down XP normally anymore, I had to end all the processes in the taskmanager to force it to restart.  When it rebooted I got into Ubuntu and was able to access all of my files on the NTFS partitions.

---

