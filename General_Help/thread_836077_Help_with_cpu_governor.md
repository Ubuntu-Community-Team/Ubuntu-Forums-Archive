---
title: "Help with cpu governor"
date: 2008-06-21
forum: General Help
---

### Post by killersnowgoon on 2008-06-21
hi, i have a sony vaio vgn-fz490 with a intel t8300 processor (2.40ghz, dual core). i have the cpu governor set to "ondemand". the lowest setting it 800mhz, but i would rather the lowest be 1.20 ghz. is there anyway to change the settings?

---

### Post by starscalling on 2008-06-21
sudo dpkg-reconfigure gnome-applets

say yes to suid

add cpu frequency monitor to panel

left click on it and select the radio button you like

---

### Post by killersnowgoon on 2008-06-21
thanks

---

### Post by ramjet_1953 on 2008-06-21
A couple of things to consider, before playing with the speed governor.

1. Laptops are hot little suckers and running your CPU at a rate that the system does not require will increase the CPU temperature quite dramatically.

2. Increasing CPU speed also consumes more power, not only for the CPU, but also for the fan, which is trying valiantly to cool it down.

3. The whole reason for the on-demand setting is to minimise temperature and power use, with little, or no noticeable loss in performance.

What do they say about trying to fix something that isn't broken????

Regards,
Roger :cool:

---

