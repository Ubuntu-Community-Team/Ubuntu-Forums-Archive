---
title: "Getting a ClamAV error"
date: 2022-03-30
forum: General Help
---

### Post by tfors2005 on 2022-03-30
I'm trying to setup ClamAV on 20.04.4 LTS and I keep getting the error message 

Wed Mar 30 11:02:49 2022 -> !LOCAL: Could not create socket directory: /var/run/clamav: Permission denied
Wed Mar 30 11:02:49 2022 -> !LOCAL: Socket file /var/run/clamav/clamd.ctl could not be bound: No such file or directory

And when I try 

mkdir /var/run/clamd.scan

[FONT=arial]It tells me that the directory can't be made, the permission is denied even though I am the root user and I'm signed in.
My question is, how do I get around the "Permission Denied" answer and continue setting up ClamAV?
[/FONT]

---

### Post by ActionParsnip on 2022-03-30
What is the output of:
```

apt-cache policy clamav

```
Thanks

---

### Post by ActionParsnip on 2022-03-30
[https://www.howtoforge.com/community/threads/clamd-will-not-start.34559/](https://www.howtoforge.com/community/threads/clamd-will-not-start.34559/)

Seems the magic reboot can fix it, or something about editing config files.

---

### Post by tfors2005 on 2022-03-30
> **ActionParsnip said:**
> What is the output of:
```

apt-cache policy clamav

```
Thanks

Output is:

clamav:
  Installed: 0.103.5+dfsg-1~20.04.1
  Candidate: 0.103.5+dfsg-1~20.04.1
  Version table:
 *** 0.103.5+dfsg-1~20.04.1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 Packages
        100 /var/lib/dpkg/status
     0.102.2+dfsg-2ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 Packages

---

### Post by tfors2005 on 2022-03-30
> **ActionParsnip said:**
> [https://www.howtoforge.com/community/threads/clamd-will-not-start.34559/](https://www.howtoforge.com/community/threads/clamd-will-not-start.34559/)

Seems the magic reboot can fix it, or something about editing config files.
 
 Reboot just gives me another error:

ERROR: /var/log/clamav/clamav.log is locked by another process
ERROR: Can't initialize the internal logger

---

