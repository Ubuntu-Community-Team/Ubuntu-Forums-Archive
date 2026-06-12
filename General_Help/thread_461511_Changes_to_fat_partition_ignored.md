---
title: "Changes to fat partition ignored"
date: 2007-06-01
forum: General Help
---

### Post by nico08 on 2007-06-01
Hi,

I have a dual-boot Windows XP and Xubuntu setup. I'm using a FAT32 partition to share data between the two operating systems. It has worked well, but recently I've noticed that when I copy files to the shared partition, the files disappear after I reboot. I've tried manually unmounting the drive after I make changes, but the problem still happens. If anyone has any suggestions of how to try to fix this, I'd appreciate it. Thanks.

---

### Post by steevols on 2007-06-01
In which OS are you having the problems? I know that Windows has difficult seeing changes if you hibernate, boot in Linux (and copy files), and then thaw Windows, but I've never heard of any other issue.

---

### Post by smoker on 2007-06-01
just some thoughts, have you checked amount of used disk space to acertain whether the files are actually gone, or just cannot be seen? have you ticked the box to reveal hidden files? did you copy them as one user, and are looking for them logged in as another?

---

### Post by nico08 on 2007-06-16
Thanks for the help. Just in case anyone else encounters this, I believe the problem was due to returning from hibernation in Windows XP after writing changes to the drive in Ubuntu. Once I started shutting down in Windows rather than hibernating, the problem went away.

---

### Post by cinci on 2007-06-30
Hi everyone,

I have the similar problem.

hiberante linux -> start/wake up windows -> make changes on the shared fat partition -> shut down / hibernate windows -> wake up linux,

Now the changes are not recognised by linux. Unmounting and mounting again does not help. But after restarting the  linux completely the changes are seen.

This is awkward. How to force system to have a look on the disk without restarting?

Cheers !

---

