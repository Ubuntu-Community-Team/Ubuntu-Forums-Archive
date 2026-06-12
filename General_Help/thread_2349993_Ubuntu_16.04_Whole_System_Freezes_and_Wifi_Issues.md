---
title: "Ubuntu 16.04 Whole System Freezes and Wifi Issues"
date: 2017-01-20
forum: General Help
---

### Post by Alvyn_Velazquez on 2017-01-20
Hello there,

This is my last resort and as I am typing this, the whole system is freezing intermittently. Anyways, when I had first dual-booted Ubuntu and Windows everything was fine until recently I've started to have issues with the system. The problem I'm having is that my system will completely freeze up (Mouse and everything) about every 30 seconds. And the eventuallly after freezing up so much the Wifi will just stop working altogether. Now I'm starting to think that this is a problem with the Wifi Adapter drivers because when I plug in the Ethernet cable, everything works smoothly. However I'm not sure how to fix this Wifi issue. 

Here are some details about the Laptop, and let me know if you need anything else to help with this problem.

Computer Model: HP 17-p110nr

When I run this command I get this:
aeosgames@Xxaeos-HP:~$ dmesg | grep rtl
[   17.605646] rtl8188ee 0000:01:00.0: enabling device (0000 -> 0003)
[   17.612892] rtl8188ee: rtl8188ee: Power Save off (module option)
[   17.612896] rtl8188ee: rtl8188ee: FW Power Save off (module option)
[   17.612919] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   17.803401] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   17.803768] rtlwifi: rtlwifi: wireless switch is on
[   17.854792] rtl8188ee 0000:01:00.0 wlo1: renamed from wlan0

---

