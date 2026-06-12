---
title: "Apt-get error"
date: 2008-06-05
forum: General Help
---

### Post by Bigtime_Scrub on 2008-06-05
I ran ```
sudo apt-get install gkrellmd
```
What does it mean?
I got back this:

gary@gary-desktop:~$ sudo apt-get install gkrellmd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gkrellmd
0 upgraded, 1 newly installed, 0 to remove and 26 not upgraded.
Need to get 73.1kB of archives.
After this operation, 213kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe gkrellmd 2.3.1-1ubuntu2 [73.1kB]
Fetched 73.1kB in 16s (4568B/s)                                                
Selecting previously deselected package gkrellmd.
(Reading database ... 175640 files and directories currently installed.)
Unpacking gkrellmd (from .../gkrellmd_2.3.1-1ubuntu2_i386.deb) ...
Setting up gkrellmd (2.3.1-1ubuntu2) ...
Warning: The home dir /var/run you specified already exists.
Adding system user `gkrellmd' (UID 112) ...
Adding new user `gkrellmd' (UID 112) with group `nogroup' ...
The home directory `/var/run' already exists.  Not copying from `/etc/skel'.
adduser: Warning: The home directory `/var/run' does not belong to the user you are currently creating.

gary@gary-desktop:~$

---

### Post by rraj.be on 2008-06-05
i got the same out put now when i tried to solve it for you.

I think the package is trying to replace  /var/run.


But i cant detect why.

Better file a bug report because the same result came for me when i tried with 6 diffrent computer's.

---

### Post by pointone on 2008-06-05
It's creating a user "gkrellmd" with the home directory "/var/run" while the home directory should probably be "/var/run/gkrellmd".

---

