---
title: "/dev/null : permission denied error"
date: 2007-03-06
forum: General Help
---

### Post by dzul1983 on 2007-03-06
Hi all
I'm using Ubuntu 6.10 and I've been having this problem for the past 2 days.. and I think it might have something to do with my system being a little bit unstable.. if I leave the PC on overnight in either XP or Ubuntu, it locks up when I try to use in the morning.. but a simple reset usually fixes this.. however lately it's been a bit different..

I booted up one morning and found myself looking at a terminal login instead of the Gnome login.. I thought nothing of it at first and so I logged in with my username and password at the terminal.. only to get this output

/dev/null : permission denied

repeated over and over in terminal.. I could stop it with Ctrl+C but startx won't boot into X Windows.. someone suggested chmodding the /dev/null with 666 permission but that didn't help and I still couldn't boot into X.. I searched around and found someone suggesting me to reinstall coreutils, dpkg and libc6.. I tried doing them all in one go, but got this message instead..

sudo apt-get install --reinstall coreutils dpkg libc6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/2993kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  coreutils dpkg
Install these packages without verification [y/N]? y
E: Couldn't configure pre-depend coreutils for dpkg, probably a dependency cycle.

I find that I can't use basic commands such as ls, cp or mv.. I tried chrooting into the drive using the LiveCD but to no avail.. my USB keyboard stopped working the moment I get to the terminal login after booting..

I'm posting this via LiveCD.. Is there any way I can repair or recover the system? If it makes any difference, I'm using the XFS file system.. below are my system specs

AMD Athlon 64 3000+
1GB DDR400 RAM
MSI K8N Neo2 Platinum m/b
Inno3d 6600GT videocard
Maxtor 80GB IDE HDD
Hitachi 320GB SATA HDD

please help..

---

### Post by dzul1983 on 2007-03-06
bump..

---

### Post by amphet on 2007-03-06
try

sudo /etc/init.d/gdm start

---

### Post by dzul1983 on 2007-03-06
didn't work either.. I finally gave up and reinstalled Ubuntu.. making sure I separate the /home folder onto a different partition.. and since I could access the / partition, I just moved all my files onto a different partition..

thanks anyway..

---

