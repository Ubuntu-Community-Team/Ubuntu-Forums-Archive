---
title: "Watching TV on Ubuntu"
date: 2006-10-17
forum: General Help
---

### Post by 13warrior on 2006-10-17
Hi,

After scraping through nearly all the threads related to watching TV on linux , infinite searchs on GOOGLE , I am left with no other choice but to cry out for help. 

I have a Techcom TV Tuner Card and after trying out lspci and dmesg made few inferences - Its based on the philips saa7130 chipset . Please help me out in this issue. I tried using both TVTIME and MythTV ( which is slightly complicated).

---

### Post by fragos on 2006-10-17
First question is there a driver loaded.  Try lsmod|grep saa and see if anything come up.  If not I have no experience with your chip set but you will need a driver which you will have to modprobe to get running.  The second isuue may be identifying the tuner.  If your saa7130 driver can't recognize which tuner you have it will default tuner to 0 whcih won't work.  Let us know what you find.

---

