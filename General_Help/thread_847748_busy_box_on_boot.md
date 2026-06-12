---
title: "busy box on boot?"
date: 2008-07-02
forum: General Help
---

### Post by Kdawkins on 2008-07-02
hey all,

So I used wubi toady to install Ubuntu 64 inside of my Vista 64. I am able to boot into the live CD and everything works okay. 

However, when I boot into Ubuntu via the windows boot loader, I get the Busy Box thing that comes up. 

I am running a Nvidia Nforce 790i ultra chipset with 3 500 gig drives in RAID 5... Could that be the issue?

I have tried booting with pci=nomsi and irqpoll, but nothing works... 

any ideas?

Thanks,
Kevin

---

### Post by fjgaude on 2008-07-03
I can't see how under Ubuntu the fakeraid5 is going to be recognized. When you dual-boot the Windows driver for the raid is not loaded. Anyway, this is my take on this. No raid5!

---

### Post by avtolle on 2008-07-03
Look at [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) for some answers, one of which is that the RAID-5 has to go (at least to install).

---

### Post by Kdawkins on 2008-07-04
ahh I cant do that.... I have too much info (I am using about 50% of my terabyte). I just bought VMWare workstation though, and it is working great!

Thanks,
Kevin

---

