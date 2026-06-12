---
title: "to those who assembled 6.06.1 - please explain"
date: 2006-11-27
forum: General Help
---

### Post by peter@kkvs on 2006-11-27
The Ubuntu people who assembled the server edition of Dapper appear to have left out the module pam_smbpass.so. :evil: 

Without this programs like swat will not modify the passwds properly.

Please explain where is pam-smbpas.so, how can you get it and install it  
OR
What is the alternative to tell PAM to look at tdbsam to find the samba passwd backend.

---

### Post by K.Mandla on 2006-11-27
Is this what you're after?

[http://packages.ubuntu.com/dapper/admin/libpam-smbpass](http://packages.ubuntu.com/dapper/admin/libpam-smbpass)

I'm thinking you can install it with *sudo aptitude install libpam-smbpass*, but I've never worked with that, so I might be way off course. ;)

---

### Post by peter@kkvs on 2006-11-28
Thanks, found it now.
It was another one of those little bits (along with smbclient and others) that did not get installed along with samba but is integral with it. 
I wish those who prepare these distros could appreciate that if they want people to migrate to linux then they need to do a better job of preparing the distribution.
Programs that are part of something like samba either need to be installed with it or at least documented in the ubuntu server guide that these programmes need to be installed separately with a description of their function. 
I would have thought that smbclient and smbfs should be installed with samba. That netkit-inetd, ssl, stunnel would be installed with swat with preconfigured conf / login files that lesser mortals could modify.
No we are left to flounder on the internet trying to find the odd line to write or the odd program to add it to fix a simple problem that never needed to be a problem.

---

### Post by K.Mandla on 2006-11-28
Good points. If you feel very strongly about it, you could [file a bug report]("http://www.launchpad.net/malone") and give your rationale as a description. You might find some support among other samba fans.

There's a similar push afoot to have [build-essential]("http://packages.ubuntu.com/edgy/devel/build-essential") installed by default, since there are any number of compilation tricks that need it. So it appears on the desktop and alternate CDs, but you have to install it manually before you can get anything started. A minor point to some, but a major bone of contention if you need it from the get-go. Cheers and good luck. ;)

---

