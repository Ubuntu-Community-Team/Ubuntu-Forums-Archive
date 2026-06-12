---
title: "Ubuntu MATE 15.10 Bitdefender crash &amp; virus engines not loading"
date: 2016-03-19
forum: General Help
---

### Post by joop3 on 2016-03-19
Im Running Ubuntu MATE 15.10 with Bitdeffender and have only solved the problem of the antiviurs crashing when you try to scan and engine not loading temporarily running AVCORE v2.1 linux x86_64 11.0.1.12 oct 13 2015 virus engine version
by running this script in terminal as sudo or administrator.

  cat /opt/BitDefender-scanner/var/lib/scan/versions.dat.* |awk '/bdcore.so.linux/{print $3}'|while read bdcore_so;do touch /opt/BitDefender-scanner/var/lib/scan/$bdcore_so;bdscan --update;ln -s /opt/BitDefender-scanner/var/lib/scan/$bdcore_so /opt/BitDefender-scanner/var/lib/scan/bdcore.so;done

rm /opt/BitDefender-scanner/var/lib/scan/bdcore.so
ln -s /opt/BitDefender-scanner/var/lib/scan/bdcore.so.linux-x86_64 /opt/BitDefender-scanner/var/lib/scan/bdcore.so

all together with the space. just copy pasted.

then I launch Bitdefender in terminal with

sudo bdgui

I want to know if there is a permanent fix so i dont have to copy paste all this text every time I run bit defender.

---

### Post by sammiev on 2016-03-19
This all needs to be run as root.

All support for Bitdefender Linux ended Dec 31/15 for desktops.

---

### Post by joop3 on 2016-03-20
Anyone know of good free anti virus beside bitdefender  or clamav.

---

