---
title: "unable to install ubuntu"
date: 2016-09-16
forum: General Help
---

### Post by swreg-k on 2016-09-16
Hello,

I'm trying to install ubuntu 16.04, the CD boots then I get the purple screen with the keyboard and little man, then the screen goes black 
and I get the messages below.

I have taken the CD to other computers and it boots with no issues.

I have various versions of windows on my system and they all boot up with no issues. I using Bootit Bare metal . I created 2 partitions for ubuntu, the native and the swap

My boot drive is utilizing raid 0

Any Ideas what I need to try?


[3.8] device-mapper table: 252:2: striped couldnt parse stripe destination
[3.9324991] device-mapper table: 252:4: striped couldnt parse stripe destination
[34.939679] ata9.00 exception emask 0x52 sact 0x0 serr 0xffffffff action 0xe frozen
[34.9397001] ata9: serror: {recovdata recovcomm unrecovdata persist proto hostint phyrdychg phyint commwake 10b8b dispar badcrc handshk linkseq trstatrns unrecfis devexch]
[34.939734] ata9.00: failed command: identify packet device
[34.939748]  ata9.00 cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 4 pio 512 in   
[34.939748] res 40/00:00:00:00:00/00:00:00:00:00/00 emask 0x56 (ata bus error)
[34.939779] ata9.00: status: {drdy}

---

### Post by swreg-k on 2016-09-16
Hello,

I'm trying to install ubuntu 16.04, the CD boots then I get the purple  screen with the keyboard and little man, then the screen goes black 
and I get the messages below.

I have taken the CD to other computers and it boots with no issues.

I have various versions of windows on my system and they all boot up  with no issues. I using Bootit Bare metal . I created 2 partitions for  ubuntu, the native and the swap

My boot drive is utilizing raid 0

Any Ideas what I need to try?


[3.8] device-mapper table: 252:2: striped couldnt parse stripe destination
[3.9324991] device-mapper table: 252:4: striped couldnt parse stripe destination
[34.939679] ata9.00 exception emask 0x52 sact 0x0 serr 0xffffffff action 0xe frozen
[34.9397001] ata9: serror: {recovdata recovcomm unrecovdata persist  proto hostint phyrdychg phyint commwake 10b8b dispar badcrc handshk  linkseq trstatrns unrecfis devexch]
[34.939734] ata9.00: failed command: identify packet device
[34.939748]  ata9.00 cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 4 pio 512 in   
[34.939748] res 40/00:00:00:00:00/00:00:00:00:00/00 emask 0x56 (ata bus error)
[34.939779] ata9.00: status: {drdy}

---

### Post by irv on 2016-09-16
How old a PC are you trying to install it on? What are the specs? Unable to boot sometimes requires the right kernel appropriate for your CPU. This might be the problem but I can only guess.

---

### Post by Jimysbil on 2016-09-16
I think you should check [this]("https://bbs.archlinux.org/viewtopic.php?id=174335") out.
You could try to connect your drive to another SATA port on your motherboard but I am not 100% sure it would be the solution as long as we are talking about a raid.
If you change a SATA port you should probably rebuild your raid.

---

### Post by speedwell68 on 2016-09-17
Will it boot from a USB memory stick?

---

### Post by coffeecat on 2016-09-17
Duplicate threads merged. Please do not cross-post.

---

### Post by swreg-k on 2016-09-17
Hello,

System is a Asus Intel core(TM) i7-4770 CPU # 3.50ghz, 3501 MHZ, 4 Cores, 8 Logical Processors
Bios American Megatrends inc 8/15/2014

And I've tried from a memory stick same issue

---

### Post by RobGoss on 2016-09-17
It would help if you provided the specs for your machine because it helps others give the best advise possible, Ram, CPU, Disk space, Graphic card

---

### Post by swreg-k on 2016-09-17
Below are the systems scpec

Ram                                                          32 GIG
disk Space avail on boot drive                        221 GIG
Graphic Card                                               AMD Radeon Rd 200 Series
CPU                                                          Asus Intel core(TM) i7-4770 CPU # 3.50ghz, 3501 MHZ, 4 Cores, 8 Logical Processors

---

### Post by swreg-k on 2016-09-19
any ideas how to resolve my issue ?

---

### Post by RobGoss on 2016-09-19
Have you try another version of Ubuntu to see it loads up to the desktop environment? Sometimes not all Ubuntu's ISO's play nicely on some machines 

You said you also try a USB drive and it did not load correctly how and what did you use to create that USB drive?

---

### Post by swreg-k on 2016-09-19
I have tried 3 different version of Ubuntu and all had the same issue.

I don't recall what tool I used to create the usb drive, is their a recommended one to use ?

---

### Post by RobGoss on 2016-09-19
> **swreg-k said:**
> I have tried 3 different version of Ubuntu and all had the same issue.

I don't recall what tool I used to create the usb drive, is their a recommended one to use ?

Are you using Windows to create the USB bootable drive? you can use Rufus to create your USB it's one I see used a lot and I see more people rely on [https://rufus.akeo.ie/](https://rufus.akeo.ie/) I use the software that Ubuntu / Linux provides because they work very well

---

