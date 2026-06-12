---
title: "check filesystem error"
date: 2006-10-21
forum: General Help
---

### Post by [seif] on 2006-10-21
At loading, after check /home:

> Log of fsck -C -R -A -a 
Sat Oct 21 13:01:24 2006

fsck 1.39 (29-May-2006)
/home contains a file system with errors, check forced.
/home: Inodes that were part of a corrupted orphan linked list found.  

/home: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
fsck died with exit status 4

---

### Post by lloyd_b on 2006-10-21
You need to unmount that filesystem, and then run "fsck" on it.

Note: The following assumes that you're talking about a desktop machine.  If it's a server (with other people using it) then the "unmount" command below will probably fail with a "Device or resource busy" message. 

In a terminal window:
[B]cd /
df[/B]

Using this info, find the device ("/dev/hda2" "/dev/sdb1", etc) associated with "/home".  

[B]umount /home
fsck {device}[/B]

where {device} is that value you got from the "df" command.  

When fsck finished:

**mount /home**

This should clean that up.

Lloyd B.

---

### Post by [seif] on 2006-10-21
It is'nt server? but:
> ~$ sudo umount /home
Password:
umount: /home: device is busy


---

### Post by lloyd_b on 2006-10-21
> It is'nt server? but:
Quote:
~$ sudo umount /home
Password:
umount: /home: device is busy 

That's why I had that "cd /" at the beginning of those instructions.  If *you* are currently in a subdirectory of that filesystem, then the "umount" command will also fail.

I can tell you didn't cd to the root directory because your prompt shows as "~$", rather than just "$" :-)

But come to think of it, you might just have that problem even if you aren't in your home directory.  If so, try booting into "Recovery Mode" (It should be an option in the GRUB menu on startup).  From there you should be able to umount/fsck without any problems.

Lloyd B.

---

