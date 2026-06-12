---
title: "Ubuntu keeps freezing, requires hard reboot"
date: 2015-05-09
forum: General Help
---

### Post by diane8 on 2015-05-09
My dell latitude E5530 is running 15.04 vivid 64bit and im constantly getting entire system freezes.
The system freezes have occurred on all versions of ubuntu starting with trusty 14.04.1 LTS all the way up to vivid 15.04.
The only difference between my laptop and the stock E5530 from dell is my upgraded 500gb Hybrid SSHD and 8gb of corsair vengeance RAM, all other specs are.....

-Intel Core i5-3210M CPU @ 2.50GHz
   Intel Ivybridge Mobile 
500gb Seagate Momentous SSHD
8gb Corsair Vengeance RAM

Kernel Version - 3.19.0-16-generic
Also im not using any Nvidia hardware so its not a GPU conflict
Here are 2 screenshots that i dont know what to make of...one error and an unknown device/driver..
[ATTACH=CONFIG]261873[/ATTACH][ATTACH=CONFIG]261872[/ATTACH]

---

### Post by dino99 on 2015-05-10
when things goes wrong, think to glance at logs: xorg.0.log and syslog/dmesg or 'sudo journalctl' to find something usefull explaining that issue
A freeze is mostly due to the graphic driver (most of the time), but can also concern plugin(s) or swap

Glancing at your snapshot, it clearly explain your freezing issue:  google around the 'drm intel error' shown, it might help you find solution across forums (also check Dell forum)

---

