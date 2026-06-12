---
title: "Multi-Boot Ubuntu's on Desktop as ‘Removable-Storage-Drives'"
date: 2018-04-19
forum: General Help
---

### Post by al14 on 2018-04-19
I Multi-boot different variants of Ubuntu on #5 seperate drives-
 
I ran-out of Intel SATA Ports, so I moved a couple of drives (#1 SSD and #1 Mechanical HDD) over to the GSATA Ports on my motherboard, and configured GSATA in the BIOS for &#8216;AHCI&#8217; , not RAID-


When any variant of Ubuntu loads from a Drive in an Intel SATA Port, the drives on the GSATA Ports appear on the desktop as &#8216;Removable-Storage-Drives'-


The GSATA is Marvell (88SE9172) driven-


When I unmount either of them , I get the following error messages:


**Error ejecting /dev/sdf: Command-line &#8216;eject &#8221; /dev/sdf&#8217;&#8217;&#8217; exited with non-**
**zero exit status 1:eject: unable to eject, last error: Inappropriate ioctl**
**for device**


*They mount as &#8216;Removable-Storage-Devices&#8217;, but they will unmount despite the error message...

Thanks in advance!

---

### Post by al14 on 2018-04-21
Due to 'a 'Lack-Of-Interest', I liberated all the drives from GSATA Ports, and I 'repatriated' them to their 'native' Intel SATA Ports-

They seem very pleased and happy to be back!

Thanks to everyone for taking the time to read this sad story, although it does end on a happy note! :P

---

### Post by oldfred on 2018-04-21
Is this a new name for Asmedia ports?
Asmedia ports have not worked at all with Linux in the past, and if one port was used, often system would not work at all.
[https://rog.asus.com/forum/showthread.php?23363-Asmedia-or-Intel-sata-6-0-Gb-on-maximus-v-formula-which-is-best](https://rog.asus.com/forum/showthread.php?23363-Asmedia-or-Intel-sata-6-0-Gb-on-maximus-v-formula-which-is-best)

---

