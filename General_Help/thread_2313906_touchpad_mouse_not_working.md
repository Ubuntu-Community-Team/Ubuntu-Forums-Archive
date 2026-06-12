---
title: "touchpad mouse not working"
date: 2016-02-16
forum: General Help
---

### Post by nikkifraser92 on 2016-02-16
I recently updated to ubuntu 15.10 and ever since strange things have been happening. When I first upgraded the touch-pad worked. Yesterday, I woke up the screen (the monitor was just turned off not suspend or hibernate) and my touchpad is suddenly dead. I have a usb mouse plugged in and have it working in the mean time but i really need my touchpad back since i use this laptop at work and home and most times cannot have a hard surface. My laptop is an Acer Aspire 7739. Here is the output of ```
cat /proc/bus/input/devices
``` I have tried to find an answer on several sources but came up empty. please help! thank you


```
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=4000 0 0 0 0


I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
U: Uniq=
H: Handlers=event2 
B: PROP=0
B: EV=21
B: SW=1


I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 
B: PROP=0
B: EV=120013
B: KEY=10000 c0200 0 0 0 0 0 700f 2000003 3802078 f870f401 febfffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input11
U: Uniq=
H: Handlers=kbd event5 
B: PROP=0
B: EV=3
B: KEY=3e000b 0 0 0 0 0 0 0


I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio2/input0
S: Sysfs=/devices/platform/i8042/serio2/input/input10
U: Uniq=
H: Handlers=mouse1 event7 
B: PROP=9
B: EV=b
B: KEY=6420 0 30000 0 0 0 0 0 0 0 0
B: ABS=2608000 11000003


I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Acer WMI hotkeys"
P: Phys=wmi/input0
S: Sysfs=/devices/virtual/input/input15
U: Uniq=
H: Handlers=rfkill kbd event8 
B: PROP=0
B: EV=13
B: KEY=1c0000 0 0 0 0 0 0 0 0 16008 c00 0 300000 0 0 0 0
B: MSC=10


I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Acer BMA150 accelerometer"
P: Phys=wmi/input1
S: Sysfs=/devices/virtual/input/input16
U: Uniq=
H: Handlers=event9 js0 
B: PROP=0
B: EV=9
B: ABS=7


I: Bus=0003 Vendor=064e Product=d214 Version=0100
N: Name="WebCam"
P: Phys=usb-0000:00:1a.0-1.3/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input17
U: Uniq=
H: Handlers=kbd event10 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0 0 0 0


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel MID Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input18
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=10


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel MID Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input19
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=4


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel MID HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input20
U: Uniq=
H: Handlers=event13 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0003 Vendor=045e Product=0040 Version=0110
N: Name="Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)"
P: Phys=usb-0000:00:1a.0-1.4/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/0003:045E:0040.0002/input/input21
U: Uniq=
H: Handlers=mouse0 event6 
B: PROP=0
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

```

---

