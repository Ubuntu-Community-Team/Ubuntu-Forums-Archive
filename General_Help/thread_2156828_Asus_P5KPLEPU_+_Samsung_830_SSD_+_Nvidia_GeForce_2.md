---
title: "Asus P5KPL/EPU + Samsung 830 SSD + Nvidia GeForce 210 = SIGSEGV problems ?"
date: 2013-06-23
forum: General Help
---

### Post by yannlossouarn on 2013-06-23
Hi !

I am quite a long term Ubuntu user (AFAICR my first install was with Breezy), and I realize my setup has been quite unstable for some months. I cannot really tell when it started, and what is the cause, but :
- I had to abandon the Nvidia proprietary drivers, which caused me a lot of trouble a few months ago after a kernel update,
- I have frequent SIGSEGV crashes on various processes.

My software setup is quite a fresh one, and I suspect some changes I made on my hardware setup could be the cause of my problems :
- after a motherboard failure, I changed for an Asus P5KPL/EPU motherboard, and a Nvidia GeForce 210 based graphics board,
- my main disk is now a Samsung 830 SSD.

I did not find obvious clues showing this hardware could cause problem, and I do not have the skills for troubleshooting deeper. Any idea of the way I could check my system ?

Best regards,
Yann

---

### Post by dino99 on 2013-06-23
Breezy: wow thats a long run  :p :p
if your system has not been reinstalled from scratch recently (due to many dist-upgrades), then its the good time to use again the latest gparted from Saucy (or partedmagic) to get a clean partition(s); and dropped the orphans and other borked config settings left behind. Otherwise clean the room as much you can: clean/autoclean/autoremove/gtkorphan/bleachbit.

if the issues persist, then you need to isolate the possible source(s) to find the real problem: video driver (switch to nouveau for testing), memtest, checkbox, fwts

---

