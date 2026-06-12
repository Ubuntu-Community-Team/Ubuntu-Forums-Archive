---
title: "vsFTP - HELP! How to set different directory permissions?"
date: 2008-05-12
forum: General Help
---

### Post by ruipedroca on 2008-05-12
Hi,

I'm setting a vsFTP server in an Ubuntu server 8.04 (with Gnome installed).
Anyone can point me the way to set different permissions to different directories to the same user? 

Everything is working fine, users can log in, upload and download. But i whished that in some folders they could only read.
I've played around with the commands in the vsftpd.conf and everything seems ok.

Example:
user A, logs in and sees two folders: one to which he can read/write and other he can only read.

Regards!

---

### Post by Monicker on 2008-05-12
Have you tried using chmod and chown to adjust the permissions?

```
chown DirA username
chown DirB username

chmod u+rw DirA
chmod u+r DirB
```

The above would give the user read/write access to DirA, but only read access to DirB.

---

### Post by ruipedroca on 2008-05-12
Hi,

Thanks, Monicker! 
I was wondering if i could do it just using ftp commands, because it seems to me they are much more fine grained (like denying LIST, RNTO, RNFR and others to specific users).

And there's also this problem: how to chown - and chmod, by the way - new files automatically?
i've posted this question here: [http://ubuntuforums.org/showthread.php?t=792055](http://ubuntuforums.org/showthread.php?t=792055)

Regards!

---

