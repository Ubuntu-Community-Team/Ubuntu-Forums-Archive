---
title: "Ubuntu Feisty on Dell E1505"
date: 2007-04-28
forum: General Help
---

### Post by Amol_Karmarkar on 2007-04-28
Hello,

I am thinking of purchasing a Inspiron E1505 and intend to dual boot with Ubuntu 7.04 (feisty) and run Aero and Beryl. I want to minimize the tweaking I will need to do post installation and I hope everything will work out of the box since E1505 is shown as compatible with Ubuntu in the Ubuntu HCL ( [http://doc.gwos.org/index.php/DellLT](http://doc.gwos.org/index.php/DellLT) ). The configuration I am looking at is :

Inspiron E1505 Intel® Core™ 2 Duo T5600 (1.83GHz, 2MB L2 Cache, 667MHz FSB)
Operating System Genuine Windows Vista™ Home Premium
LCD Panel 15.4 inch UltraSharp™ Wide Screen SXGA+ Display with TrueLife™
Memory 2GB Shared Dual Channel DDR2 SDRAM at 533MHZ, 2 DIMM
Video Card 256MB NVIDIA® GeForce® Go 7300 TurboCache*
Hard Drive 80GB 5400rpm SATA Hard Drive
Network Card Integrated 10/100 Network Card and Modem
DVD+RW Drive 8X CD/DVD Burner (DVD+/-RW) with double-layer DVD+R write capability
Sound Options Integrated Audio
Wireless Networking Dell Wireless 1390b/g (54Mbps)
Primary Battery 53 WHr 6-cell Lithium Ion Primary Battery

I intend to use the laptop mostly for the usual stuff - word processors, spreadsheets, music, movies, browsing, photo editing, downloads etc and will generally use Ubuntu though I might need to end up using Vista occasionally. I do not play computer games at all. I needed advise on my configuration and I want to optimize it considering that my budget is limited and I want the laptop to last for atleast 3 years.

1) What processor must I choose ? Does Intel Core2 Duo T5600 ( 1.83 GHz ) offer significant performance improvements over Intel Core Duo T2350 (1.86 GHz) ?

2) What video card I must choose ? I am totally confused between Intel GMA 950 / ATI Radeon X1400/ NVidia GeForce Go 7300. I would like some eye candy on my desktop and want to run Aero and Beryl. Is there a significant difference when watching movies / running "eye candy" stuff like Aero / Beryl between Intel GMA 950 and ATI / NVidia cards ? What video card drivers run best on Ubuntu ? Should I get a bigger hard drive plus a 9 cell 80 WHr battery by sacrificing the NVidia Video card ?

3) Shall I go for Dell Wireless 1390b/g or Intel PRO/Wireless 3945a/g ? I hear that people are facing issues with Dell Wireless card in Ubuntu. Which card is well supported in Ubuntu Feisty and will work out of the box ? Or do I need to resort to tricks ( like using ndiswrapper ) to make it work for both cards ?

Kindly advise.

Regards,
Amol

---

### Post by elephant007 on 2007-04-28
I own a Dell E1505 laptop, originally ran Edgy then upgraded to Feisty via updates not from the install CD.

 1.  As far as Core 2 Duo and Core Duo, the major differences is that the Core 2 Duo is a 64bit processor where the Core Duo is a 32bit.  Other differences might be that L2 Cache sizes, I'm not sure though.  Go with whatever processor you think is the best value.

2.  I went with the ATI Radeon Mobility X1400 256MB.  It runs Beryl and Aero without problems. Remember that because the ATI says it's a 256MB on the card, it actually has 128MB onboard and shares 128MB of system memory.  If you get the ATI, I'd suggest using the Open Source drivers and not the one provided from the ATI website.  I guess this is just by preference.

3.  Got WiFi?  The one integrated with my laptop is the Broadcom 4311.  I used ndiswrapper to use the driver provided by Dell backed by Gnome-Network-Manager.  My wireless works wonderfully well.  It is possible that other integrated WiFi will be automatically configured by Feisty Fawn so you wouldn't need to use ndiswrapper or other means to get the card working.  You should probably research on this to find out for sure.  I was playing around with Feisty Fawn Live CD at work, put it in a D600 Dell laptop, it found the wireless card and configured it, all i had to do was configure the card to connect to the wireless network at work and I was off and running surfing the internet.

  One draw back I've experienced is that the resolution isn't as tight as it was in Vista.  1280x800 is what I'm running in Ubuntu.  I dumped Microsoft Vista altogether, I won't even dual boot with that flawed operating system that took 7+ years to develop...

  To sum it all up, you will NOT be disappointed running Ubuntu on the laptop.  You may experience great difficulties with Vista though.

Good Luck to ya!

---

