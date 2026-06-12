---
title: "How to mount a multi-user disk partition at boot time"
date: 2022-05-31
forum: General Help
---

### Post by Ralph L on 2022-05-31
I am trying to install Xubuntu 22.04 and having a bad time with it. First, running the live memory stick with Jammy clobbered my existing system in a separate memory partition, but that's another story. My current problem is the /etc/fstab seems to have been removed. In my previous systems I made an entry in fstab for a shared_data partition. This partition contains data for multiple users. Previously (using fstab) it always mounted as /media/shared_data. This allowed all users to use it (their own folders). Now it mounts as /media/username/shared_data and doesn't seem to be available to all users. Is there a new "fstab" someplace???? Is there some other way I can mount shared_data for multiple users???

any help appreciated....

---

### Post by TheFu on 2022-05-31
The fstab still works as it always did.  I haven't seen any difference in my 22.04 install.

The first question is which file system is on the partition you wish to mount?  With Linux native file systems, the answer is much easier.

---

### Post by yancek on 2022-06-01
The /media directory is usually used for removable devices.  Is this partition on the same hard drive as your OS?  I doubt your /etc/fstab has been removed, simple enough to check.  You should be able to gives permissions to each user to access his/her directories and files unless it is a windows partition.  Have you checked the permissions on the different user directories as well as /media/username?

---

### Post by Ralph L on 2022-06-01
I want to thank you guys for responding to a dumb question. I am embarrassed to say what I did wrong. I looked for /etc/fstab as a folder, not a file. How dumb can you get??? Anyway, you guys saying fstab was still there prompted me to do a proper search and I found it, updated it to mount automatically mount my shared_data partition under /media and its working.
Thanks again.....

---

