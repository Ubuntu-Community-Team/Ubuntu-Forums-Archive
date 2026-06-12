---
title: "Modifying an md array online"
date: 2013-06-29
forum: General Help
---

### Post by georgesgiralt on 2013-06-29
Hello !
I've an historic server running now 12.04 and having the following configuration inherited from distant past :
3 disks (now 320G sata ) because at one time it used LVM mirroring.
Each disk is partitioned as follow :
First partition around 200 MB in size tagged md raid
Remaining space tagged md raid.
The 3 first partition are made into md0 mirror which was formatted EXT2 and is used as /boot.
The 3 second partition are made into a 3 legged mirror also and subsequently used as the sole PV in the volume group onto which all LV are set up for the server. 
The 200 MB /boot is a PITA now. So I would like to extend the 3 first partition on the disks up to around a couple of gigs and set them into md0 as they were. 
As this is a production server and quite critical, doing it without disrupting service nor loosing any data is mandatory. ;-)
I'm proficient in LVM and md raid but would like to get your advice on how you would do it. All pertinent ideas are worth hearing before committing to the work.... 
Many thanks in advance for your help and answer. 
Have a bright day !

---

