---
title: "SFTP and permissions"
date: 2013-04-03
forum: General Help
---

### Post by alfirdaous on 2013-04-03
Hello everybody,

While transferring files using SFTP, directories are set to 755 persmissions and files to 664, I would like to set them to 751 and 644 alternatively after the transfer is done, how can I proceed with that??

Thanks in advance

---

### Post by Lars Noodén on 2013-04-03
You can look up [umask](http://manpages.ubuntu.com/manpages/precise/en/man8/sftp-server.8.html) in the manual page for the sftp-server.  You would then set the umask in [/etc/ssh/sshd_config](http://manpages.ubuntu.com/manpages/precise/en/man5/sshd_config.5.html), if you have access to the server.  If you don't have access, then you need to work it out with the system administrator.

---

### Post by alfirdaous on 2013-04-03
I found [this tuto]("http://retout.co.uk/blog/tags/sftp"), but it does NOT work :(

It stays at 664

EDIT: I change the 002 to 022, it works for files (644) but directories are still in 755 instead of 751

---

### Post by rnerwein on 2013-04-03
> **alfirdaous said:**
> I found [this tuto]("http://retout.co.uk/blog/tags/sftp"), but it does NOT work :(

It stays at 664

EDIT: I change the 002 to 022, it works for files (644) but directories are still in 755 instead of 751

hi
i ain't know - but i think in the tutorial there is something misrememberd. --> restart the vfstd ??!
ciao
ups - i forgot - the changes must be made on the target side and sorry i mean /usr/sbin/vsftpd

---

### Post by alfirdaous on 2013-04-03
what is vfstd?

---

