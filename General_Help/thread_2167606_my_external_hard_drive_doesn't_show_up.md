---
title: "my external hard drive doesn't show up"
date: 2013-08-14
forum: General Help
---

### Post by AbhimanyuAryan on 2013-08-14
I was using the same ext. hard drive on my laptop running ubuntu 13.04 and it used to work fine but today after i updated ubuntu......the hard drive doesn't show up in the side bar nither in home/        

for more details i am using this ext. hard drive:[http://www.sony.co.in/product/hd-e1/sku/hd-e1_pc2+ww1](http://www.sony.co.in/product/hd-e1/sku/hd-e1_pc2+ww1)

i have checked this hard drive on my pc running windows7 and it works fine...........plz help

---

### Post by Boab1993 on 2013-08-14
Hi[SIZE=2][FONT=arial][[COLOR=#000000]AbhimanyuAryan[/COLOR]]("http://ubuntuforums.org/member.php?u=1833246")[/FONT][/SIZE], 

Try finding out if your system detects your device, open a terminal session and type:

```
 lsusb 
```

Post your results here.

---

### Post by AbhimanyuAryan on 2013-08-14
> **Boab1993 said:**
> Hi[SIZE=2][FONT=arial][[COLOR=#000000]AbhimanyuAryan[/COLOR]]("http://ubuntuforums.org/member.php?u=1833246")[/FONT][/SIZE], 

Try finding out if your system detects your device, open a terminal session and type:

```
 lsusb 
```

Post your results here.

this is what i got 

cooldudeabhi@cooldudeabhi-Studio-1450:~$ lsusb
Bus 001 Device 003: ID 0c45:6407 Microdia 
Bus 002 Device 006: ID 054c:05bf Sony Corp. 
Bus 002 Device 005: ID 1bbb:0017 T & A Mobile Phones 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 004 Device 004: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 004 Device 005: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth
cooldudeabhi@cooldudeabhi-Studio-1450:~$

---

### Post by Boab1993 on 2013-08-14
> Bus 002 Device 006: ID 054c:05bf Sony Corp. 

That appears to be your external HDD, so it is being recongnised.

[FONT=arial]Try typing ```
[/FONT][FONT=arial]gconftool --set /apps/compiz-1/plugins/unityshell/screen0/options/devices_option  --type=int 1
```

Into the terminal and see if it re-appears in the sidebar
[/FONT]
[FONT=arial][/FONT]

---

### Post by AbhimanyuAryan on 2013-08-14
> **Boab1993 said:**
> 

[FONT=arial]Try typing [/FONT]```
[FONT=arial]gconftool --set /apps/compiz-1/plugins/unityshell/screen0/options/devices_option  --type=int 1[/FONT]
```[FONT=arial]

Into the terminal and see if it re-appears in the sidebar
[/FONT]


nothing happens i got this in terminal

cooldudeabhi@cooldudeabhi-Studio-1450:~$ gconftool --set /apps/compiz-1/plugins/unityshell/screen0/options/devices_option  --type=int 1
cooldudeabhi@cooldudeabhi-Studio-1450:~$

---

### Post by AbhimanyuAryan on 2013-08-15
> **Boab1993 said:**
> That appears to be your external HDD, so it is being recongnised.

[FONT=arial]Try typing [/FONT]```
[FONT=arial]gconftool --set /apps/compiz-1/plugins/unityshell/screen0/options/devices_option  --type=int 1[/FONT]
```[FONT=arial]

Into the terminal and see if it re-appears in the sidebar
[/FONT]


mate i worked for me........but its too slow it showed up after 5 mins i connected it.......any solutions

---

### Post by VMC on 2013-08-15
Unplug USB device, then monitor syslog using this:

```
tail -f /var/log/syslog
```

After you start monitoring, re-insert the USB device, and wait for the 5-min time. Copy/Paste results back here.

---

