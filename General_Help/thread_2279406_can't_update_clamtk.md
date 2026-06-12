---
title: "can't update clamtk"
date: 2015-05-23
forum: General Help
---

### Post by Jaladhi_R_Trivedi on 2015-05-23
can't update clamav from terminal
```
 jaladhi@jaladhi-Compaq-510:~$ sudo freshclam
[sudo] password for jaladhi: 
ERROR: /var/log/clamav/freshclam.log is locked by another process
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).
jaladhi@jaladhi-Compaq-510:~$ 

```
How to fix it?

---

### Post by Vladlenin5000 on 2015-05-23
The error is a consequence of its database being in use, accessed by other processor which isn't other than the ClamTK daemon itself.
This ancient thread provides a solution that should still work but _unless you made ClamTK a startup app/service_ - it isn't by default and there's absolutely no valid reason to have an AV running all the time, if at all, like in Windows - a simple reboot or even log out/log in should do the same.
[http://ubuntuforums.org/showthread.php?t=1032147](http://ubuntuforums.org/showthread.php?t=1032147)

---

### Post by boopa0705 on 2015-05-23
[https://code.google.com/p/clamtk/](https://code.google.com/p/clamtk/)    here you wil find the update..

---

### Post by Vladlenin5000 on 2015-05-23
> **boopa0705 said:**
> [https://code.google.com/p/clamtk/](https://code.google.com/p/clamtk/)    here you wil find the update..

No.

The method you already tried is the correct one. The reason for the error and the fix is in my previous post. At the above web page which, by the way, is being discontinued, you'll find the main program. You don't need it because you already have it installed and the program itself don't require updates, its database does like any other AV.

New users (and others not-so-new) should always be **strongly** advised against installing software outside the Ubuntu repositories, even different versions of the same software found in the official repos.

---

### Post by Jaladhi_R_Trivedi on 2015-06-18
Thanks @vladlenin5000 could update clamav. thanks

---

### Post by Jaladhi_R_Trivedi on 2015-06-18
only thing is that after starting again not able to update so had to keep daemon stopped

---

