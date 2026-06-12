---
title: "Mount drive within mounted drive"
date: 2007-09-05
forum: General Help
---

### Post by likwid on 2007-09-05
Hi

I have two large hard drives used for storing various media and would like very much if i could mount the second within the mounted structure of the first. Is this possible? Certainly, using fstab would present a problem as it's likely the first would not be mounted in time. How about a boot time script, is it possible to implement a delay on it running?

Thanks in advance.

---

### Post by likwid on 2007-09-05
Hmm. Seem to have solved my own problem, there was no problem. I had problems previously with this but now it's fine. Oh well, case solved for me..

---

### Post by likwid on 2007-09-05
OK. Now i do have a problem. 

I can mount a drive in a directory of another drive, however, when i share said parent folder with nfs the child folder is empty.

Any ideas?

---

### Post by zekica on 2007-09-05
NFS has this problem/feature that it can only export files from one volume. You'll have to share the other volume separately.

---

### Post by tonym on 2007-09-05
This is  a "feature" of NFS.  See descripition of nohide option in "man exports".

---

### Post by likwid on 2007-09-07
Thanks for help. In the end i just shared the child mount and remounted it within the mounted parent folder from the other machine.

---

### Post by likwid on 2007-09-10
One more thing actually. I would like to mount a network share in my home directory Documents folder. This seems not to work using fstab, unless i umount -a after boot.

Cheers!

---

### Post by vanadium on 2007-09-10
It seems you urgently should learn about using symbolic links instead of mounts to access your data. Just mount a device once in your file system, then use symlinks to be able to access the data from wherever you want. For example

ln -s /mnt/network_drive_1 /home/mynetworkdata

will create a link mynetworkdata to your mounted network drive. For practical user purposes, such a symbolic link fully behaves like a normal directory.

---

### Post by likwid on 2007-09-10
Cool, thanks

---

