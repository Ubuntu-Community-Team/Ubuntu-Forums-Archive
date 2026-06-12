---
title: "Can't mount FreeBSD/pfSense disk"
date: 2016-02-03
forum: General Help
---

### Post by abator on 2016-02-03
sudo mount -r -t ufs -o ufstype=ufs2 /dev/sdc1 /home/myprofile/somedir

Results in some general error. I found through demesg | tail this message:

ufs: ufs_fill_super(): bad magic number

I'm completely new to Linux but i googled that it may mean that disk is corrupted.
But it boots system normally.
Anything can be done to mount this disk on Ubuntu?
I actually only need to copy it's data.

---

### Post by ajgreeny on 2016-02-03
Please tell us what you did to solve this problem and then use the Thread Tools menu at the top to mark the thread as solved.

The forums are used by many Ubuntu users and it is in the spirit of the forum for solutions to be posted when found so that other users with the same problem can search and find it.

We do not delete threads or posts in normal situations.

---

