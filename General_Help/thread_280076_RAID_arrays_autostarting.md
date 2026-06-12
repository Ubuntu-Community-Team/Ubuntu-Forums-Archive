---
title: "RAID arrays autostarting"
date: 2006-10-18
forum: General Help
---

### Post by bforbes on 2006-10-18
I have two 200g hard drives that I want set up as a RAID1 array. I have got it to work using mdadm, but there are things happening that I don't completely understand. Whenever I boot up, two RAID devices are created, /dev/md0 and /dev/md1. /dev/md0 is a RAID0 array using the same two 200g hard drives, and /dev/md1 is the correct RAID1 array. I can't find any configuration file that has details for the RAID0 array. Why is it being created?

I also removed /etc/mdadm.conf, which had the RAID1 details in it, but the arrays are still created whenever the computer boots! Why is this happening?

---

### Post by bforbes on 2006-10-19
I tried clobbering the hard drives using dd, but this /dev/md0 RAID0 array keeps getting built when the computer starts. The hard drives no longer have raid autodetect partition types. Does anyone know what's going on here?

---

