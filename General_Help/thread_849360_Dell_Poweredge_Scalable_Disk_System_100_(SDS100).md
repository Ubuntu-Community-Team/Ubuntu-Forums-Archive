---
title: "Dell Poweredge Scalable Disk System 100 (SDS100)"
date: 2008-07-04
forum: General Help
---

### Post by djh82uk on 2008-07-04
Hi All 

I have the above storage array

I can install ubuntu on it, but it only goes onto one of the HDD's, how can I choose if I want raid 0 or raid 1?

Dell do not do a lnix based tool, is there anyway to do this?  The on board scsi adapter (MB) is AIC-7880 based.

I am not very good with scsi stuff, and esspecially not storage array's

Can anyone help?

Thanks

DJH

---

### Post by fjgaude on 2008-07-05
I don't know anything about the array you have... to use the drives in an array and have Ubuntu loaded would require a driver which I'm sure Adaptec will never make.

The only avenue for you would be to use software raid, using **mdadm**... and simply use the drives in the box as drives, having **md** in the Ubuntu kernel as the array assembler.

Unless you need raid for a reason and are willing to spend time learning about software raid0 and raid1 I would forget the whole thing.

---

### Post by cariboo on 2008-07-05
Most scsi card manufacturers have linux drivers, your card should be supported out of the box, run lspci in a terminal and paste the output in your next post.

I have a Mac G3 running Xubuntu 8.04 with an Adaptec scsi card and it was detected and modules installed right of the box.

Jim

---

### Post by fjgaude on 2008-07-05
It's one thing to have the SCSI card recognized, but another to be able to use that card to create a raid0 or raid1 array for use with Ubuntu. You will need a special driver and I've not ever noticed an Adaptec raid driver for .deb-based Linux systems. 3ware, yes, but not Adaptec. Adaptec does have drivers for .rpm-based systems, like RedHat and SUSE. Some change that using **alien** you can convert the .rpm file to a .deb one.

---

