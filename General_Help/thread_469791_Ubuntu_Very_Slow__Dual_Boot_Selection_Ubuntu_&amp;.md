---
title: "Ubuntu Very Slow / Dual Boot Selection Ubuntu &amp; XP"
date: 2007-06-10
forum: General Help
---

### Post by bcurtis7 on 2007-06-10
I am fairly new to the Ubuntu and Linux community.  I am setting up my computer to have Windows XP and Ubuntu.  
I have a twofold question.  I just installed Ubuntu on a separate hard drive, and it seems to be loading and running very slowly.  I set it up on a fairly quick system, as follows:

P4 3.2 HT processor
Asus P4P800SE motherboard
4 gig PC-3200 ram
ATI Radeon 800XT video card
Soundblaster X-Fi Gamer soundcard
2 - 120g IDE hard drives Raid 0 on PCI raid card (Windows installation)
1 - 40g IDE hard drive (Ubuntu Installation)

I let Ubuntu automatically set up and format the 40 gig hard drive as my linux drive during installation, but I remember reading somewhere that the swap drive should be 2x the amount of ram in a system.  It is currently at 1600MB, should I have manually set it up to 8000MB?
What is happening at boot up of Ubuntu is that I hang up on this line:

Starting Hardware abstraction layer hald

It will hang for about 5 minutes or so before finally booting up into Ubuntu, and then Ubuntu runs painstakingly slow.

I also see this during boot up:

[ 69.743592] I/O error on device sbd1 logical block 480214784

The above repeats roughly 20 times or so before and after i see the abstraction layer hald with different addresses and logical blocks

Now my second question is about how to be able to select my OS during boot up.  Currently I have to change my hard drives in the BIOS, but I would like to be able to choose them at boot up.  Is this possible and how would I go about it.

Thanks in advance.
bcurtis7

---

### Post by hessiess on 2007-06-10
> ATI Radeon 800XT video card

that would be your problem ;)

---

### Post by bcurtis7 on 2007-06-10
> **hessiess said:**
> that would be your problem ;)

Can you elaborate a little more?

---

### Post by hessiess on 2007-06-11
im no expert, but ati cards work verry porly under linux, becose of poor drivers. you can use ati cards and linux, but you will probaly get bad proformance.

try the gag bootloder. it should work.

from what i have red the swap needs to be about half your total ram. unless you are rendering extremly detaliled 3d modals you will never use 1600mb of ram. so you dont need mutch swap.

waght for somone more experiansed to anser your thred. have you tryed to install drivers for the ati?

---

### Post by bcurtis7 on 2007-06-11
thanks hessiess

no, i have not actually searched for a driver as of yet...
i will look into the driver issue a little more..

---

