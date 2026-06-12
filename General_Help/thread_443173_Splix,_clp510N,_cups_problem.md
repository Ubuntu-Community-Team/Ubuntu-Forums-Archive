---
title: "Splix, clp510N, cups problem"
date: 2007-05-14
forum: General Help
---

### Post by tappad on 2007-05-14
A short description of my problem..
I have installed my printer and it does work for printing pages from OpenOffice and testpages.
However as i want to print an pdf all i get is a page saying:

SPL-C ERROR - Incomplete Session by time out
POSITION : 0x10f615e (...

And some other info..

Ive found out that it's /usr/lib/cups/filter/pstoraster thats crashing. 
Im using 64-bit version.

D [14/May/2007:15:19:16 +0200] [Job 35] cupsPPD = 0x75b970
D [14/May/2007:15:19:16 +0200] [Job 35] cupsPPD->flip_duplex = 0
D [14/May/2007:15:19:16 +0200] [Job 35] width = 4908, height = 6340
D [14/May/2007:15:19:16 +0200] [Job 35] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [14/May/2007:15:19:16 +0200] [Job 35] HWMargins = [ 11.520 15.590 11.520 15.590 ]
D [14/May/2007:15:19:16 +0200] [Job 35] matrix = [ 8.333 0.000 0.000 -8.333 -96.000 6470.083 ]
E [14/May/2007:15:19:16 +0200] PID 8925 (/usr/lib/cups/filter/pstoraster) crashed on signal 11!
D [14/May/2007:15:19:16 +0200] [Job 35] [33mRaster::readLine: Cannot read image data[0m
D [14/May/2007:15:19:16 +0200] [Job 35] Wrote 7439 bytes of print data...
D [14/May/2007:15:19:16 +0200] [Job 35] Read 8192 bytes of print data...
D [14/May/2007:15:19:16 +0200] [Job 35] Wrote 8192 bytes of print data...
D [14/May/2007:15:19:16 +0200] [Job 35] Read 3424 bytes of print data...
D [14/May/2007:15:19:16 +0200] [Job 35] Wrote 3424 bytes of print data...
D [14/May/2007:15:19:16 +0200] Discarding unused printer-state-changed event...
E [14/May/2007:15:19:16 +0200] PID 8926 (/usr/lib/cups/filter/rastertospl2) crashed on signal 11!
D [14/May/2007:15:19:16 +0200] Discarding unused printer-state-changed event...
D [14/May/2007:15:19:16 +0200] PID 8927 (/usr/lib/cups/backend/socket) exited with no errors.
D [14/May/2007:15:19:16 +0200] [Job 35] File 0 is complete.

Regards!

---

### Post by klaus_zinser on 2008-02-25
Hi, up to now I have not connected the CLP-510 to Ubuntu. But I had conneced the Printer to a DLink DNS 323 Gigabit Netzwerk Storage. With Win XP64 (and also I think W2k (connected over the LAN Cable to the DNS323 I had the same error message. Finally I changed the USB Cable (the old one must had been a USB1.1 - the new one is shielded, I cant say for sure but supects it is conform to USB2). Now the printer setup works fine. 
Re your problem, first I would try the cable, then check if you have an old USB1.1 Hardware Card. If this is okay I would go for the software.

---

