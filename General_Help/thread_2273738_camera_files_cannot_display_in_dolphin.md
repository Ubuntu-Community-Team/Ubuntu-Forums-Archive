---
title: "camera files cannot display in dolphin"
date: 2015-04-15
forum: General Help
---

### Post by luke40 on 2015-04-15
My camera is Casio EXILIM 6x. It cannot display in file manager when I connect it to computer.

Any help will be much appreciated.

---

### Post by luke40 on 2015-04-19
The exact  type is **Casio EXILIM EX-ZS20.**

---

### Post by Holger_Gehrke on 2015-04-20
The last few lines of the output of the 'dmesg' command called a few seconds after plugging in the camera will show you how the kernel sees the camera and what it tried to do with it.

---

### Post by luke40 on 2015-04-23
they are:

*PROTO=TCP SPT=58277 DPT=80 WINDOW=29040 RES=0x00 SYN URGP=0 *
*[10420.812910] [UFW ALLOW] IN= OUT=ppp0 SRC=61.64.211.173 DST=91.189.94.12 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=38655 DF PROTO=TCP SPT=58278 DPT=80 WINDOW=29040 RES=0x00 SYN URGP=0 *
*[10425.250661] usb-storage 1-4:1.0: USB Mass Storage device detected*
*[10425.251030] scsi8 : usb-storage 1-4:1.0*
*[10437.357430] [UFW AUDIT] IN= OUT=ppp0 SRC=61.64.211.173 DST=91.189.94.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=38658 DF PROTO=TCP SPT=58278 DPT=80 WINDOW=227 RES=0x00 ACK FIN URGP=0 *


what next to do?

---

### Post by Geoffrey_Arndt on 2015-04-23
If your PC (laptop or desktop) has a built-in port for SD and other memory card sizes, you can just remove the SD (or whatever card) from the camera and plug it in the mmc slot on your PC.   No need to connect the whole camera via a USB cable to the PC (unless you have one of the older, now rare PC's without that slot).

So then, your camera card is seen by the PC similar to a usb-flash stick.   Then just use the file manager to copy the files where you want them.

---

### Post by Geoffrey_Arndt on 2015-04-23
Duplicate post, pls disregard.

---

