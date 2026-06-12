---
title: "help needed regarding nfs"
date: 2007-06-25
forum: General Help
---

### Post by openfreak on 2007-06-25
Hi,
Guys  recently I convinced my H.O.D at my college to allow me install linux (I chose ubuntu)on one comp.But I want my friends and my professors to use it and get acquainted with it .But the problem is no one wants to try out a dual boot system in one place --they are aprehensive about the system stability etc etc...you know typical windows users.

Now I want to set up a nfs root such that it canbe booted of a bootable cd, I can have individual home partitions on the fat/ntfs file system.

I can manage to get 100-200MB of the HDD where  I can put  the minimum root file system and take most the program over the nfs  with /home on windows partition.


"This way  more people use linux and may ultimately accept it."

The average configuration of the computers at my college is 
P-4 2.8Ghz             128MB RAM             40GB HDD             100mbps LAN

---

### Post by rklauco on 2007-06-25
You are looking for pxe boot server with DHCP etc.
A lot of info can be found on wiki - check out:
[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)
[https://help.ubuntu.com/community/DisklessSimple](https://help.ubuntu.com/community/DisklessSimple)

---

