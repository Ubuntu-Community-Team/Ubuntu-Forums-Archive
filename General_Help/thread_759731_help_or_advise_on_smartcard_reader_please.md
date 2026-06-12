---
title: "help or advise on smartcard reader please"
date: 2008-04-19
forum: General Help
---

### Post by Arther_dent on 2008-04-19
Hi this is my first post and after my first week of using ubuntu 7.10 I only have one question/problem:)
my dell laptop has a o2micro usb reader built in,lsusb from the cli reveals this 
Bus 001 Device 007: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
question is...can this be intalled under ubuntu? ie is there a driver available?
any help with this would be appreciated.

---

### Post by y-lee on 2008-04-19
I found [O2-Micro Oz776 SmartCard Reader]("http://manx.biz/opensource/Dell-M65/TPM.html") on google. Hopefully it will help :)

---

### Post by prshah on 2008-04-19
> **Arther_dent said:**
> 
my dell laptop has a o2micro usb reader built in,lsusb from the cli reveals this 
Bus 001 Device 007: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
question is...can this be intalled under ubuntu? ie is there a driver available?


I have an O2 Micro Bay module in my Fujitsu LifeBook, and it's supported out-of-the-box in Gutsy. In fact, it doesn't work properly in XP; (I can only use it with the command line), but works great in gutsy.

---

### Post by Arther_dent on 2008-04-20
Cheers y-lee :) will try and sort it using that info later today.


prshah \: it def does not work for me from a clean install when i do lsusb from cli i get this output

Bus 001 Device 004: ID 046d:c043 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 005 Device 011: ID 07b4:0112 Olympus Optical Co., Ltd MAUSB-100 xD Card Reader
Bus 005 Device 008: ID 413c:8126 Dell Computer Corp.
Bus 005 Device 010: ID 0a5c:4503 Broadcom Corp.
Bus 005 Device 009: ID 0a5c:4502 Broadcom Corp.
Bus 005 Device 004: ID 07ab:fcd2 Freecom Technologies
Bus 005 Device 006: ID 0a5c:4500 Broadcom Corp.
Bus 005 Device 007: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 005 Device 005: ID 0b97:7761 O2 Micro, Inc.
Bus 005 Device 002: ID 413c:a005 Dell Computer Corp.
Bus 005 Device 001: ID 0000:0000


i can identify all the devices except 

Bus 005 Device 008: ID 413c:8126 Dell Computer Corp.
Bus 005 Device 010: ID 0a5c:4503 Broadcom Corp.
Bus 005 Device 009: ID 0a5c:4502 Broadcom Corp.

Bus 005 Device 006: ID 0a5c:4500 Broadcom Corp.
Bus 005 Device 007: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 005 Device 005: ID 0b97:7761 O2 Micro, Inc.
Bus 005 Device 002: ID 413c:a005 Dell Computer Corp.

I dont know but i assume the dell components are something to do with the usb its self the broardcom I think is bluetooth(which I never use) and the two o2 micro devices are the built in smartcard reader

anyhoo keep the suggestions coming...

---

### Post by Arther_dent on 2008-04-22
for any one else who is trying to get a card reader  working and has checked this thread it seems like ive been barking up the wrong tree!
this device is seen by ubuntu as a pci device not usb as i stated above doh!
yes im a noob when it comes to linux :( you might say ive come back from the darkside after 13years as a M$ user(Slave?),so bear with me please....
lspci from the cli gives

03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
 now ive found 1 or 2 threads with instructions on enabling the SD slot but i need the xD picture card and Memory stick slots but I cant find any info on these.

any ideas kind people?

---

### Post by Goyf on 2008-05-19
up

---

