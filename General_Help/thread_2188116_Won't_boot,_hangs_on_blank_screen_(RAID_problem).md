---
title: "Won't boot, hangs on blank screen (RAID problem)"
date: 2013-11-15
forum: General Help
---

### Post by gnaget on 2013-11-15
I have an ubuntu server 12.04.  It contains 2 raid array, one hardware raid 1 for the system, and one software raid 5 for storage.  I believe one of the drives on the storage raid 5 dropped out, and caused the system to crash.  Now, it is stuck on a black screen when I try to boot with no error.  

I can boot into a live cd, and drop into a shell on the system raid 1, so I don't believe that is the problem.  mdstat shows the raid 5 as inactive, and commenting out the array line in /etc/mdadm/mdadm.conf has no affect.  

First off, is there a problem with my config somewhere that would cause a storage array, with no system files on it, to prevent my server from booting?

Second, how do I get this thing to boot up again?

---

