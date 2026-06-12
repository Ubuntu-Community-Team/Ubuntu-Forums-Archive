---
title: "onbord os Flash or boot from SD card"
date: 2016-07-18
forum: General Help
---

### Post by selvamurugan on 2016-07-18
Hi ,


I have on board like Advantech UBC-220 model.Its already contains linux kernel 3.0.35 inside.

I have checked with tera term Its booting and can view some files.

It has on 4 GB internal memory and 1 GB of RAM.

they were loaded on board linux in NAND.

This board contains  SD CARD option,HDMI,USB,OTG ,LAN ports.

My question is how to boot from sd card or how load os on internal memory  .

manufactures provuded some BSP package on their web.I cant extract that rar file in UBUNTU 10.04 LTS and other version ,windows like.

I am interfacing this UBC-220 board to my PC and through serial port and checking basic information via hyper terminal.

So any one give me the instruction for installing OS at Advantech UBC-220.


just i want to boot os form SD card or on board  mem whenever its power up

---

### Post by selvamurugan on 2016-07-27
I have received correct image file from the supplier and YOCO linux is the correct package for this model ..

---

### Post by C.S.Cameron on 2016-07-27
You should be able to install Ubuntu to SD just like installing to internal drive.
When you get to partitioning make sure you install the system and grub to the correct drives. 
Ubuntu will mainly run from RAM, except when booting a program for the first time that session.
Installing Ubuntu to internal memory will take more than 4GB unless making a Persistent install.
In which case mkusb does a good job.

---

