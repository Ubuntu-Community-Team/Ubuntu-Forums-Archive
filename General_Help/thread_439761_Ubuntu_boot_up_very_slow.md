---
title: "Ubuntu boot up very slow"
date: 2007-05-11
forum: General Help
---

### Post by jesschen on 2007-05-11
I have installed bootchart. When I viewed  the chart, It tooks system 2.58 minutes to load desktop enviroment. 

Now, I would likes to know that how why after modprobe, both ata_id and vol_id , together tooks more than 2 minutes.

here is my computer spec
Pentium 4 3.00GHz
20GB IDE
200GB SATA
DVDRW

---

### Post by donkyhotay on 2007-05-11
First thing I have to ask is what version of ubuntu are you running? When I first upgraded to feisty I had a similar issue. For some reason when I ran 32bit feisty with my 64bit processor it slowed up there too. I eventually switched to 64bit feisty and haven't had any issues with it.

---

### Post by jesschen on 2007-05-11
Thanks for the fast response, I am using 32bit. when I use ubuntu 6.10, it also takes long time to boot, Since I use ubuntu  6.10, I thought thats is normal, until recently, I founded bootchart on the website.

by the way, I install ubuntu on 20GB hard disk

---

### Post by jesschen on 2007-05-11
Note that I had attached the lastest bootchart

---

### Post by Matty2006 on 2007-05-11
Looking at your chart.. it looks like there is something going on with establishing your mounted volumes or maybe something that has to do with the controlling your hard drive.

based on the chart.. it looks like modrpobe is getting a workout then there is all this time with your volumes.

Personally I don't really understand how this stuff works together.. maybe something in your hardware is not fully established or happy with the drivers its given or maybe your volumes are dirty and under-go cleaning every time you boot.

I have a chart sort of like this but it is caused by my Wifi configuration and dhcp running out.. Not sure how to stop dhcp on boot up.. 

Good luck with this.

---

### Post by jesschen on 2007-05-12
Last two days, I had playing BIOS, trying with so many possibility, still does not have any luck.

I had researched Modprobe and ubuntu, I still does not understand it all. 


My really last option is to unplug the SATA hard disk.

---

