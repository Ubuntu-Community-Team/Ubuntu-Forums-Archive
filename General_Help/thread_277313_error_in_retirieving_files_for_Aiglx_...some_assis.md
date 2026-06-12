---
title: "error in retirieving files for Aiglx ...some assistance"
date: 2006-10-14
forum: General Help
---

### Post by hyby on 2006-10-14
hi i can not seem to download a file for aiglx installation following the wiki guide.

 	    	
hyby@hyby:~$ sudo aptitude install xserver-xorg-air-core linux-dri-modules-common linux-dri-modules-`uname -r`
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "linux-dri-modules-2.6.15-27-386"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

i was wondering can i get some assistance

---

### Post by trickykungfu on 2006-10-14
I was just having the same problem.  Googling "aiglx 2.6.15-27" yielded this page: [http://www.hermies.net/downloads/](http://www.hermies.net/downloads/)

...which has the package you need.  Install it using dpkg -i, or just double-click it.

---

