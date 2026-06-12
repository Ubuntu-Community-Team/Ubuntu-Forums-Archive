---
title: "Question about Raid-0"
date: 2008-05-08
forum: General Help
---

### Post by alexv305 on 2008-05-08
I am thinking about buying two VelociRaptor 300GB Drives. There supposed to be really good drives so I want to Raid-0 two of them and see the performance. My question is: If I set up a Raid-0 Array and Make two partitions one for windows and the other for Ubuntu, will ubuntu 8.04 autodetect the Raid or would I need to pre-install some linux drivers for it to recognize the array?

Thanks.

---

### Post by the-edmeister on 2008-05-09
How are you intending to implement RAID? Hardware or software? You might want ask that question at a support forum for your brand of motherboard, or the RAID controller card you would be using.

---

### Post by fjgaude on 2008-05-09
There's really no way to boot into a raid0 partition unless it has been already assembled before the OS is being read. This can only be done with a hardware card with raid driver for the version of ubuntu you are to install.

---

