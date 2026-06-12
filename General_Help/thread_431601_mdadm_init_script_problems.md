---
title: "mdadm init script problems"
date: 2007-05-03
forum: General Help
---

### Post by jimbolaya on 2007-05-03
I am having a very frustrating time with mdadm.  

I have an md array that mdadm refuses to start up and sometimes shut down properly.  I don't know if it is because the init script is in the wrong place or if mdadm is just crappy.  

I have RAID5 array of two PATA and two SATA drives, each around 300MB.  When mdadm stops it sometimes only "unbind"s and "export_rdev"s 3 of the 4 drives.  But mostly, when it starts up at boot, it only "bind"s 3 of the 4 drives, always leaving out the first drive in the array.  I've done some thorough testing and if I unmount the directory that is on the md0 partition, and then do a stop on the array, it "unbind"s all the drives correctly most of the time.  If I assemble the array by hand after that, it seems to work fine.  So far, however, it hasn't worked once correctly on boot.  

HELP!!!!!!

James

---

### Post by gerscht on 2007-05-03
do all 4 drives have **FD** as partition type? (use fdisk and then option p to find out) This is required in order to auto detect the drives on boot.

---

