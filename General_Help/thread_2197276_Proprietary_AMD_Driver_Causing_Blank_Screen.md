---
title: "Proprietary AMD Driver Causing Blank Screen"
date: 2014-01-03
forum: General Help
---

### Post by Incarnadine on 2014-01-03
I just recently installed the "AMD Catalyst™ 13.12 Proprietary Linux x86 Display Driver" video card driver for Ubuntu 13.10 Desktop (64-bit). I executed the .run file from Terminal and restarted the computer when prompted. When Ubuntu attempts to load now, the screen is blank and my mouse cursor is a white "X". Is there a reason why this is happening?

I tried to install the driver provided from the official AMD website because I was getting a watermark on the lower right hand corner of my screen saying "Hardware Unsupported." I figured the latest driver would fix this problem. I guess I was wrong :( Now I'm forced to use my Windows partition to post this problem. Help me guys! [-o<

---

### Post by lisati on 2014-01-03
*Thread moved to **General Help**.*

The "Forum Feedback and Help" section is for requesting help using the forum.

---

### Post by Mark Phelps on 2014-01-03
> Is there a reason why this is happening?Could be that the AMD drivers are incompatible with your video card and Ubuntu 13.10.

If you don't know what make and model card you have, then boot from an Ubuntu LiveCD/LiveUSB, open a terminal, enter the command "lspci" (without the quotes) -- and look for the line containing "VGA".  Post that info back here.

---

### Post by Incarnadine on 2014-01-04
My video card is an AMD Radeon R9 Series. The driver I downloaded from the AMD website was specifically for my video card.

---

### Post by guy12 on 2014-04-01
Hi, just wondering if anyone has found a fix for this problem since I am having the same exact issue. Any help would be appreciated. Thanks in advance!

---

### Post by Mark Phelps on 2014-04-01
The R9 series are very new and are not well supported in the AMD fglrx drivers yet.  Sorry, but you're stuck with the open source drivers until AMD finally gets around to releasing the fglrx drivers.  That's the price you pay for having very new hardware in Linux.

---

### Post by guy12 on 2014-04-01
Thanks so much for the quick response! I was hoping that wasn't the case due to all the movement of cards today. If you wouldn't mind another question, I think I know the answer but should I completely remove the AMD driver before going open source. Once again, thanks!

---

