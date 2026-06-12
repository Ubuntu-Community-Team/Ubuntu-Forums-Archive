---
title: "Boot without attached display"
date: 2014-02-02
forum: General Help
---

### Post by Petr_Kejval on 2014-02-02
Hello, how should I set up Lubuntu 13.10 for boot without attached display?

I tried multiple tutorials around internet but Lubuntu's boot hangs every time without attached display. :confused:

This Lubuntu machine is meant as DLNA, Samba, Web, RDP server so I need start X for RDP clients. Everything is set up and working fine except boot. Please help me. :(

Hardware:
Gigabyte GA-J1800N-D2H
4 GB RAM
1TB WD RED HDD ext4 partition

---

### Post by jeanjd63 on 2014-02-02
Hello
You can try on menu grub (Shift at boot if not display) 
Then "e" on the first line and on line :
"linux  /boot/vmlinuz......  quiet splash"
you change "quiet  splash"  by "text"
Lubuntu would boot in console mode (no graphic).

---

