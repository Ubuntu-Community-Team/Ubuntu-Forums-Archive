---
title: "Kompozer publishing hangs"
date: 2008-02-03
forum: General Help
---

### Post by n2stc on 2008-02-03
Kompozer seems to work fine for me other than when I try to publish it hangs forever.  I've tried all different combos of user/password/directory to no avail.  File-zilla uploads to the same FTP site no problem.

---

### Post by dcstar on 2008-02-04
> **n2stc said:**
> Kompozer seems to work fine for me other than when I try to publish it hangs forever.  I've tried all different combos of user/password/directory to no avail.  File-zilla uploads to the same FTP site no problem.

The Publishing Server FTP site location should be very specific - it should be the directory you log into when the FTP server accepts you user and password.

Apparently Kompozer also only uses Passive mode FTP, so if your FTP server is Active mode only then this may be the issue - in that case you cannot use Kompozer!   :-(

---

### Post by n2stc on 2008-02-04
> **dcstar said:**
> 

Apparently Kompozer also only uses Passive mode FTP, so if your FTP server is Active mode only then this may be the issue - in that case you cannot use Kompozer!   :-(

Sounds like this is the case. An empty file of the desired name is created.  Thanks for the reply.

---

