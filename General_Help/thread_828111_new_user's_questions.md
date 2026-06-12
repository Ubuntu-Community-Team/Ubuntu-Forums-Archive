---
title: "new user's questions"
date: 2008-06-13
forum: General Help
---

### Post by mhh91 on 2008-06-13
i have a SATA hard drive and i wanted to install ubuntu 8,but i wanted to know first if my drives will be detected using the live CD,or do i have to use the alternate CD instead for my drives to be detected

---

### Post by issih on 2008-06-13
I very much doubt that it would make any difference which cd you used as to whether the sata drives are useable. The kernel which drives the hardware once booted past bios is almost bound to be the same. I can say that ubuntu happily installed on my sata drive from a live cd. The only trouble I'm aware of was someone who had sata drives running from an add in pci card. Even then things installed fine, it was the boot loader that couldn't operate as the bios couldn't boot from the sata drive.

---

### Post by Victormd on 2008-06-13
If your only concern is the SATA drive, don't worry, ubuntu will install just fine.
Are you going to be dual-booting?

---

### Post by mhh91 on 2008-06-13
i don't think that windows is staying,as it's not working properly,also i don't have much space for it on my hard drive,by the way,my hard drive's capacity is 80GB,my C drive is 5GB,will that suite ubuntu?

---

### Post by Victormd on 2008-06-13
It all depends on how many programs you're going to be using. I would probably divide an 80GB HD like this:
boot partition: 5-10GB
swap partition: 512MB - 1GB (depending on how much RAM you have, i.e., if you have more than 1GB RAM, I'd go with 512MB swap. If you have less, probably bump that up a bit).
data files: remaining GB.

---

