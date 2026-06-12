---
title: "Ubuntu 6.10 Upgrade?"
date: 2008-06-18
forum: General Help
---

### Post by th1bill on 2008-06-18
My new dual core computer blew the processor and I installed 8.04 with no hitch but windows 2k is useless from there to me for graphics work.  I cleaned the disk and installed Win2k but the process for installing 8.04 was far beyond my ability so I  dropped back to 6.10.  My problem is that I have 7.10 and 8.04 disks but I can't find a way to begin to upgrade and get to the 8.04 that i'm seeking to run.  Is it possible?  Every time I tried to install 8.04 on the 70gig unpartitioned space on my 80gig hard drive it wanted to install without a swap partition and I did not need that headache because I work with graphics in Ubuntu also.

Any help?

---

### Post by ibuclaw on 2008-06-18
Does 6.10 have the update-manager installed?

Run
```
sudo update-manager -d
```
In the terminal and it should ask you to upgrade to a newer version number.

Regards
Iain

---

### Post by th1bill on 2008-06-19
> **tinivole said:**
> Does 6.10 have the update-manager installed?

Run
```
sudo update-manager -d
```
In the terminal and it should ask you to upgrade to a newer version number.

Regards
Iain
But whether I check from the Terminal or from System>Admin.>Update Manager there is not one available.

I am certainly willing to clean the disk once more if someone can tell me how to install 8.04 behind the Windows.

I created a 10 gig Partition for the Win2k and I just really want to wipe the 6.10 off of there and put 8.04 in it's place.  Is it possible to install Hardy now and have two Ubuntu systems without making a mess?  I still have almost seventy gig of blank hdd.

---

