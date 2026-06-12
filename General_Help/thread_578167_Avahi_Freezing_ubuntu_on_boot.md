---
title: "Avahi Freezing ubuntu on boot"
date: 2007-10-17
forum: General Help
---

### Post by Beaker Bongload on 2007-10-17
Hi, let me start with system specs

Intel Celeron D 2.53 Ghz processor
1gb ddr ram
ATI Sapphire Radeon x300se video card
Gigabyte GA-8s649-mf mobo with onboard sis 191 ethernet adapter, and  SiS 182 RIAD Controller(unused)
2 IDE 80gb HDD
I installed ubuntu 7.04 using the latest build of Wubi

I'm not a total newbie to linux here. I have successfully installed and run a ubuntu system before on another computer with no major problems or hang ups with a two disk method of duel booting with windows xp on a secondary drive with ubuntu being my primary. This computer is giving me endless problems however. I have done nothing the past  2 days but try to get ubuntu to work.

I have narrowed the problem down to either Avahi or my network card. I don't have a spare one for testing otherwise I would test that but my booting freezes on "Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon". when I disable my network card it boots fine. My question is what exactly is avahi and if it isn't vital how can I disable it from starting. I'd like to not have to go out and get a new network card to see if mine is the problem. My card is specificly supported but the 190 series of the dard IS.

Please help!

Thanks in advance

---

### Post by Beaker Bongload on 2007-10-17
well it seems it really IS my network onboard adapter. 

Sorry for all the bother. Looks like I'll need to get a new card and leave the native disabled. The system continues to freeze even with Avahi disabled. Its a shame but we'll see how the new card works when I can afford one.

---

