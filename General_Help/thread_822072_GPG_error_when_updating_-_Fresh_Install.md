---
title: "GPG error when updating - Fresh Install"
date: 2008-06-07
forum: General Help
---

### Post by janskey on 2008-06-07
Hi All,

I still have a problem on GPG error when i try to apt-get update my fresh install ubuntu and xubuntu. 

Fetched 71.6kB in 10s (6870B/s)                                                                              
Reading package lists... Done
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) hardy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems


Note: this is a fresh install, so my keys are still in default mode.

Any advice?

---

### Post by whitejohn29 on 2008-07-06
Maybe you have problem with Internet, I mean maybe it is too slow.

---

### Post by Seisen on 2008-07-07
> **janskey said:**
> Hi All,

I still have a problem on GPG error when i try to apt-get update my fresh install ubuntu and xubuntu. 

Fetched 71.6kB in 10s (6870B/s)                                                                              
Reading package lists... Done
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) hardy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems


Note: this is a fresh install, so my keys are still in default mode.

Any advice?

Go to System>Administration>Sofware Sources and click on the third-party Sofware tab, and uncheck the partner repository. Then reload your sources list and then add the partner repository again and then reload it and see if that fixes the problem. Sometimes it works to fix this problem.

---

