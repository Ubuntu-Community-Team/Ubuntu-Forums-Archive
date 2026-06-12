---
title: "mdadm from raidtools"
date: 2005-10-24
forum: General Help
---

### Post by arfon on 2005-10-24
Hello,

I have been using Suse 9.2 on a server with a raid 0 array. Suse uses raidtools by default for software raid, and so my /etc/raidtab file is below.

raiddev /dev/md0
   raid-level       0
   nr-raid-disks    2
   persistent-superblock 1
   chunk-size       32
   device   /dev/sdb1
   raid-disk 0
   device   /dev/sdc1
   raid-disk 1

I am about to update the server to Breezy and understand that Ubuntu uses mdadm rather than raidtools. I have been looking at the man pages for mdadm and I see that I need to 'assemble' my old raid to restore it. Stupid me I can't figure out the command, can someone please enlighten me??!! :p 

cheers,

arfon

---

