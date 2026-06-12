---
title: "lm_sensors help configuring temps"
date: 2015-09-22
forum: General Help
---

### Post by eliascilley on 2015-09-22
Hi everyone
 so i have been trying to get lm_sensors to read the correct temps of my CPU an MB. currently it says 0 C which would be awesome though clearly not accurate. I have left is alone for a while now but its really starting to bug me, and wouldn't you know it [www.lm-sensors.org](www.lm-sensors.org) seem to be down. is there any other way to get the information form the mb or am i stuck with it as is. 

HW rundown:
AMD A6-6420K APU 
ASUS A55bm-PLUS
Ubuntu 14.04

---

### Post by Yellow Pasque on 2015-09-22
If your Asus motherboard uses the same sensor module as this person's, this thread should be helpful: [http://ubuntuforums.org/showthread.php?t=2295342](http://ubuntuforums.org/showthread.php?t=2295342)

---

### Post by Yellow Pasque on 2015-09-22
Actually, it appears your mobo is using a Nuvoton NCT6791D.
Try this:
```
sudo modprobe -v nct6775
sensors
```

---

