---
title: "Stupidly chown-ed windows partition"
date: 2014-12-20
forum: General Help
---

### Post by enrico10 on 2014-12-20
Hello everyone, I need some help, if you could have a look.

I have a laptop dualbooting Windows 8.1 and Ubuntu 14.04.

I was trying to share some files on my home network, both from my external hard drive, and from my Windows partition, but I couldn't access it due to wrong permissions. I can't find the thread I followed, unfortunately.

I edited /etc/fstab, and added a line both for my external hard drive, and my Windows partition. Then I set the permissions with 

chmod 755 -R /media/enrico/HDD

and acquired ownership

chown enrico -R /media/enrico/HDD

Then I stupidly repeated the process on the Windows partition, so now Windows boots but crashes randomly.
Any chance of fixing my mistake?

Thanks in advance :D

---

### Post by mcduck on 2014-12-20
Chmod & chown don't do anything to windows file systems (as they don't have any way of handling POSIX ownership/permissions). So most likely the only thing your commands changed was the ownership of the mount point itself (on Linux side).

I'd bet the windows crash issues are caused by something else, so running file system check and taking a look at the log files etc. on Windows side would be a good idea.

---

### Post by pqwoerituytrueiwoq on 2014-12-20
for the sake of science i am going to try to reproduce this on a old install i have not got around to deleting
edit: test  seem to show mcduck is correct as i suspected

---

### Post by carl4926 on 2014-12-20
> **mcduck said:**
> Chmod & chown don't do anything to windows file systems (as they don't have any way of handling POSIC ownership/permissions). So most likely the only thing your commands changed was the ownership of the mount point itself (on Linux side).

I'd bet the windows crash issues are caused by something else, so running file system check and taking a look at the log files etc. on Widnows side would be a good idea.

I concur

---

### Post by enrico10 on 2014-12-21
On first boot on Windows after running the command, it reported Recycle Bin as corrupted, and having a look at the files' permissions, it seems that another user was added, who has full permissions, so I think the files were actually edited.

Plus, chmod took several hours to complete. 

I don't know what to think, I'd prefer not having to format Windows partition and reinstall everything..

---

