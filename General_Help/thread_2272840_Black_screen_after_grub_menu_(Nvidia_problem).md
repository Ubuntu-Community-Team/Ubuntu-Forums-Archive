---
title: "Black screen after grub menu (Nvidia problem?)"
date: 2015-04-08
forum: General Help
---

### Post by Demsmond on 2015-04-08
Hello everyone, I am trying to install Ubuntu on my RoG G20 desktop computer. However I am running into a problem. Whenever I try to install Ubuntu via the live USB it just gives me a black screen after I select the install method on the grub menu. I am trying to install Ubuntu 14.04LTS.

I can get ubuntu to boot but only when I disable my nvidia card in the UEFI and force to it only use the integrated intel HD graphics, however this lags with unity's fancy UI horribly so staying like this is not an option. 

I have tried installing the beta version of 15.04 to see if 14.04 was just too old for my hardware, but it just gives me a warning saying "if you try to install debian with UEFI, you could damage other OS installed on your computer i CANNOT close this error message so the installer is stuck, which is weird considering my HHD was completely empty when I tried.


[SIZE=6]NOTE : [SIZE=3]I can’t access a terminal of any kind exept for the grub terminal, so please don’t post answers asking me to run commands via ubuntu's terminal[/SIZE][/SIZE]
[B] 
My setup[/B] :  

[TABLE="class: spec-table, width: 310"]
[TR]
[TD="class: spectd"]**Processor Family:** Intel Core i5
[/TD]
[/TR]
                                          [TR]
[TD="class: spectd"]**Processor Name:** Intel Core i7-4790[/TD]
[/TR]
                                          [TR]
[TD="class: spectd"]**Processor Speed:** 3.2 GHz
[/TD]
[/TR]
                                          [TR]
[TD="class: spectd"]**RAM:** 8 GB[/TD]
[/TR]
                                          [TR]
[TD="class: spectd"]**Storage Capacity (as Tested):** 1000 GB[/TD]
[/TR]
                                          [TR]
[TD="class: spectd"]**Storage Type:** HDD
[/TD]
[/TR]
                                          [TR]
[TD="class: spectd"]**Graphics Card:** Nvidia GeForce GTX 760 / Intel HD graphics
[/TD]
[/TR]
                                          [TR]
[TD="class: spectd"]**Primary Optical Drive:** Dual-Layer DVD+/-RW
[/TD]
[/TR]
                                          [TR]
[TD="class: spectd"][/TD]
[/TR]
[/TABLE]
**Connected to a 32 inch asus monitor via HDMI**

---

### Post by gordintoronto on 2015-04-09
Have you tried nomodeset?

---

