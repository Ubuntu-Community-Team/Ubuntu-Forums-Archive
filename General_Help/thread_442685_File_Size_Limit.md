---
title: "File Size Limit"
date: 2007-05-13
forum: General Help
---

### Post by SolidCube on 2007-05-13
When I attempt to transfer large files, the transfer errors at 603 mb, throwing the error message 'File size limit exceeded: core dumped.'  

It happens as multiple users, using multiple transfer programs (FTP, scp, sftp, wget).

How do I resolve this?

---

### Post by crispy_420 on 2007-05-13
Uploading to your own server or some elses? Maybe there is a file size restriction on the other end? Ask the server admin.

---

### Post by SolidCube on 2007-05-14
this is downloading, and it doesn't matter if it's my server (I am the admin on the other end) or someone else's.   It works fine from Windows, just not Ubuntu.

Also, why would a file size restriction on the remote machine cause ubuntu to dump core?

---

### Post by russell.h on 2007-05-14
What file system are you using locally? Do any partitions on your hard drive (not just the one you are saving it too, some programs try to cache things in weird locations) have only about 603MB of space left?

---

### Post by SolidCube on 2007-05-14
No, that's not the problem.  The disk is EXT3 and has 50 megs free.

---

