---
title: "ELO Touch screen not working."
date: 2013-02-27
forum: General Help
---

### Post by crazyone on 2013-02-27
Hi I have an Acer AL1515T that uses the ELO driver. i am trying to get it working on a Ubuntu 12.04 which i ma trying to setup as a kiosk. when i run "lsusb" i get  this back 
```
Bus 004 Device 004: ID 04e7:0073 Elo TouchSystems 
Bus 008 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 008 Device 003: ID 413c:3016 Dell Computer Corp. Optical 5-Button Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
and after running "modprobe elo" and do a cat /proc/bus/input/devices i get 
```
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Dell WMI hotkeys"
P: Phys=wmi/input0
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=rfkill kbd event4 
B: PROP=0
B: EV=13
B: KEY=1500b 0 2 300000 0 0 0 0
B: MSC=10

I: Bus=0003 Vendor=413c Product=2005 Version=0110
N: Name="DELL DELL USB Keyboard"
P: Phys=usb-0000:00:1d.2-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input6
U: Uniq=
H: Handlers=sysrq kbd event2 
B: PROP=0
B: EV=120013
B: KEY=10000 7 ff9f207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=413c Product=3016 Version=1110
N: Name="Dell Premium USB Optical Mouse"
P: Phys=usb-0000:00:1d.2-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input7
U: Uniq=
H: Handlers=mouse0 event3 
B: PROP=0
B: EV=17
B: KEY=31f0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10


```


which doesnt list it at all. any help on getting this display working would be great. I dont want to have to use windows on a web only kiosk is all.

---

