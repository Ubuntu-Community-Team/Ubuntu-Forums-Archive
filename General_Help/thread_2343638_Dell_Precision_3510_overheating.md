---
title: "Dell Precision 3510 overheating"
date: 2016-11-17
forum: General Help
---

### Post by tuanctob48 on 2016-11-17
Hello guys, sorry if i post at wrong place, i have overheat problem with precision 3510 running ubuntu 14.04, temp when system idle around 50-60 celcius i dont know how to fix that! Plz help me, my room temp is about 30 celcius! Ty so much!

---

### Post by wildmanne39 on 2016-11-17
*Thread moved to **General Help**.*

---

### Post by QIII on 2016-11-17
Hello!

Would you start by giving us the hardware specs of the machine?

Thanks!

---

### Post by tuanctob48 on 2016-11-18
> **QIII said:**
> Hello!

Would you start by giving us the hardware specs of the machine?

Thanks!

Here is my specs: 
Processor
[TABLE="width: 100%"]
[TR="class: review_page_row_odd"]
[TD="width: 150"][/TD]
[TD="class: review_page_opt, width: 390"]Intel® Core™ i7-6700HQ (Quad Core 2.60GHz, 3.50GHz Turbo, 6MB 35W, w/Intel HD Graphics 530)[/TD]
[TD="class: review_page_edit, width: 10"]edit[/TD]
[/TR]
[TR="class: review_page_row_even"]
[TD="width: 150"]Chassis Options
[/TD]
[TD="class: review_page_opt, width: 390"]Intel® Core™ i7-6700HQ with USB Type C Thunderbolt Chassis[/TD]
[TD="class: review_page_edit, width: 10"]edit[/TD]
[/TR]
[TR="class: review_page_row_odd"]
[TD="width: 150"]Operating System
[/TD]
[TD="class: review_page_opt, width: 390"]Ubuntu Linux 14.04 SP1[/TD]
[TD="class: review_page_edit, width: 10"]edit[/TD]
[/TR]
[TR="class: review_page_row_even"]
[TD="width: 150"]Adobe Photo and Productivity Software
[/TD]
[TD="class: review_page_opt, width: 390"]None[/TD]
[TD="class: review_page_edit, width: 10"]edit[/TD]
[/TR]
[TR="class: review_page_row_odd"]
[TD="width: 150"]Office Productivity Software
[/TD]
[TD="class: review_page_opt, width: 390"]No Productivity Software[/TD]
[TD="class: review_page_edit, width: 10"]edit[/TD]
[/TR]
[TR="class: review_page_row_even"]
[TD="width: 150"]Video Card
[/TD]
[TD="class: review_page_opt, width: 390"]AMD FirePro W5130M w/2GB GDDR5[/TD]
[TD="class: review_page_edit, width: 10"]edit[/TD]
[/TR]
[TR="class: review_page_row_odd"]
[TD="width: 150"]Energy Star
[/TD]
[TD="class: review_page_opt, width: 390"]ESTAR Label not included[/TD]
[TD="class: review_page_edit, width: 10"]edit[/TD]
[/TR]
[TR="class: review_page_row_even"]
[TD="width: 150"]LCD
[/TD]
[TD="class: review_page_opt, width: 390"]15.6" FHD IPS Touch(1920x1080) Wide View LED-backlit(72% color gamut), camera and mic, WWAN Capable[/TD]
[TD="class: review_page_edit, width: 10"]edit[/TD]
[/TR]
[TR="class: review_page_row_odd"]
[TD="width: 150"]Memory
[/TD]
[TD="class: review_page_opt, width: 390"]16GB (2x8GB) 2133MHz DDR4 Non-ECC[/TD]
[TD="class: review_page_edit, width: 10"]edit[/TD]
[/TR]
[TR="class: review_page_row_even"]
[TD="width: 150"]Boot Hard Drive
[/TD]
[TD="class: review_page_opt, width: 390"]256GB M.2 SATA Class 20 Solid State Drive[/TD]
[TD="class: review_page_edit, width: 10"]edit[/TD]
[/TR]
[TR="class: review_page_row_odd"]
[TD="width: 150"]External Storage
[/TD]
[TD="class: review_page_opt, width: 390"]None[/TD]
[TD="class: review_page_edit, width: 10"]edit[/TD]
[/TR]
[TR="class: review_page_row_even"]
[TD="width: 150"]Wireless
[/TD]
[TD="class: review_page_opt, width: 390"]Intel® Dual-Band Wireless-AC 8260 Wi-Fi + BT 4.1 Wireless Card (2x2)[/TD]
[TD="class: review_page_edit, width: 10"]edit[/TD]
[/TR]
[TR="class: review_page_row_odd"]
[TD="width: 150"]Mobile Broadband
[/TD]
[TD="class: review_page_opt, width: 390"]No Wireless WAN Card[/TD]
[TD="class: review_page_edit, width: 10"]edit[/TD]
[/TR]
[TR="class: review_page_row_even"]
[TD="width: 150"]Keyboard
[/TD]
[TD="class: review_page_opt, width: 390"]Internal Dual Pointing Keyboard, English[/TD]
[TD="class: review_page_edit, width: 10"]edit[/TD]
[/TR]
[TR="class: review_page_row_odd"]
[TD="width: 150"]Primary Battery
[/TD]
[TD="class: review_page_opt, width: 390"]4 Cell 62W/HR Battery[/TD]
[TD="class: review_page_edit, width: 10"]edit[/TD]
[/TR]
[TR="class: review_page_row_even"]
[TD="width: 150"]Extended Service
[/TD]
[TD="class: review_page_opt, width: 390"]None[/TD]
[TD="class: review_page_edit, width: 10"]edit[/TD]
[/TR]
[TR="class: review_page_row_odd"]
[TD="width: 150"]Power Supply
[/TD]
[TD="class: review_page_opt, width: 390"]130W AC Adapter[/TD]
[TD="class: review_page_edit, width: 10"]edit[/TD]
[/TR]
[/TABLE]
 Thank you!

---

### Post by mörgæs on 2016-11-19
How hot does it get in a live boot of 16.10?

---

### Post by pqwoerituytrueiwoq on 2016-11-19
Assuming it is not full of dust bunnies, the fan is running full speed and there is adequate ventilation; i would expect this is caused by Unity (the desktop environment) keeping the GPU under load, i read that 17.04 will have a low graphics mode, using that would solve this issue by reducing the GPU load; another solution is to use a alternate desktop environment, xfce (xubuntu), mate (ubuntu mate), gnome (ubuntu gnome), kde (kubuntu), lxde (lubuntu)

Lots of laptop cooling systems use the same HSF for both the CPU and GPU so a heavy GPU load heats the CPU up

if it does not get hot on 16.10 (see above post), it is a driver support issue on 14.04 mostly likely a lack of power scaling feature for your gpu

---

### Post by tuanctob48 on 2016-11-19
thanks for your advice, i will try another DE!
P/s: i forgot this, but amd's driver only support xorg 1.16 which means proprietary amd driver's won't support on ubuntu 16.04 or later, so i should try another DE with 14.04 right?

---

### Post by pqwoerituytrueiwoq on 2016-11-20
I would try 16.04 and 16.10 on a live usb or dvd
at this point i have more faith in the open source driver than the proprietary one for AMD GPUs

---

