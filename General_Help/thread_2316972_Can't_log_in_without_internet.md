---
title: "Can't log in without internet"
date: 2016-03-12
forum: General Help
---

### Post by yavyash on 2016-03-12
I recently did a fresh install of Ubuntu 15.10, which was working fine. Shortly thereafter, I installed Windows 10 on my Windows partition on the same machine. Since then, I've been having problems logging into Ubuntu: if my computer is not connected to the Internet when I enter my password at the greeter screen, it hangs without showing my desktop until I do connect to the Internet. If I'm connected initially, whether over Ethernet or wi-fi, everything works fine.

I'm totally baffled as to how to fix this, and can't find any info elsewhere. Any suggestions?

FWIW, before I got to the point of having this problem, I had to reinstall grub from a Live Boot disk. I also encountered an issue where I wouldn't even get to the greeter screen, which turned out to be because Ubuntu was looking for a partition UUID that no longer existed. I disabled the Windows partition in /etc/fstab entirely; even replacing the UUID with the one for the new partition didn't seem to work.

---

