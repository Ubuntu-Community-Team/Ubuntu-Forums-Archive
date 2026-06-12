---
title: "Bad signature on security archive"
date: 2006-08-17
forum: General Help
---

### Post by grendel970 on 2006-08-17
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

anyone else getting this? apt-get update doesn't fix it, and I even tried deleting the security key with apt-key and then re-running update, but a no go.. I saw a posting on breezy about this with a minor difference in sources.list, but I don't see how the following would affect that:

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse

Anyone?

---

### Post by grendel970 on 2006-08-17
Never mind, it was a bad sources.list, apparently the extra / after ubuntu did it.. changing it to the following fixed it:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe main restricted multiverse

---

### Post by webjames on 2006-11-28
hi i have the same problem.

keep an eye on this thread, i hope to find a solution:

> [http://www.ubuntuforums.org/showthread.php?t=308638](http://www.ubuntuforums.org/showthread.php?t=308638)

if it is the software lists, where can you find an updated list of them?

regards,

James

---

