---
title: "apt-get update without sudo"
date: 2018-11-16
forum: General Help
---

### Post by zaheer031 on 2018-11-16
I am required to run apt-get update without prefix sudo on Ubuntu 18.04

Opened sudo visudo and added entry:

user ALL=(ALL) NOPASSWD: ALL

apt-get update gives error

Reading package lists... Done
W: chmod 0700 of directory /var/lib/apt/lists/partial failed - SetupAPTPartialDirectory (1: Operation not permitted)
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied)
Am I missing something here

Thanks for all replies

---

### Post by wildmanne39 on 2018-11-17
Why do you have to do it without sudo? please elaborate, this is a very bad idea, it puts your computer at great risk, from local users and over the internet.

---

### Post by QIII on 2018-11-17
Who is requiring this very bad idea?

---

### Post by deadflowr on 2018-11-17
You still need sudo in the command, 
All the sudoers edit did was allow it to run without the need for a password.

And +1 to the above statements about it's recklessness.

---

### Post by oldos2er on 2018-11-18
Moved to *General Help*.

---

