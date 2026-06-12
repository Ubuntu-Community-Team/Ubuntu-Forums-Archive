---
title: "No touchpad after updating to Ubuntu 13.04"
date: 2013-06-23
forum: General Help
---

### Post by Number3124 on 2013-06-23
I recently updated from Ubuntu 12.10 to Ubuntu 13.04 64-bit using MATE 1.6.0. I am using it on a Samsung RC512 laptop. It uses an Intel i7 quadcore CPU, 6 GB of DDR3 RAM, and an nVidia GT 525m (don't know if any of this is relevant). It booted up fine, but after logging in I noticed that the touchpad no longer works. I plugged in my gaming mouse, and it works just fine. The left and right buttons on the touchpad work. I ran:

```

cat /proc/bus/input/devices
```

which returned:

```
I: Bus=0011 Vendor=0002 Product=000e Version=0000
N: Name="ETPS/2 Elantech Touchpad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=1
B: EV=b
B: KEY=6420 30000 0 0 0 0
B: ABS=260800011000003
```

As far as I know, this means that the bug is not in the kernel. I lack the experience to proceed further than this. Thanks for the help.

---

### Post by Number3124 on 2013-06-24
To add some additional information, the trackpad works as it should under Windows 7 which I run in a duelboot configuration with Ubuntu and under various live CDs I pulled out to test it. It appears to only have trouble with Ubuntu 13.04. 

I'd really like to get it working again. Thanks in advance for the help.

---

### Post by Number3124 on 2013-06-29
Okay. Last try. Here are the two entries under ```
cat /proc/bus/input/devices
``` for my current mouse I'm using since the touchpad stopped working.

```
I: Bus=0003 Vendor=1532 Product=0015 Version=0111
N: Name="Razer Razer Naga"
P: Phys=usb-0000:00:1d.0-1.2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=0
B: EV=17
B: KEY=7f0000 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0003 Vendor=1532 Product=0015 Version=0111
N: Name="Razer Razer Naga"
P: Phys=usb-0000:00:1d.0-1.2/input1
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input6
U: Uniq=
H: Handlers=sysrq kbd event6 
B: PROP=0
B: EV=100013
B: KEY=1000000000007 ff9f207ac14057ff febeffdfffefffff fffffffffffffffe
B: MSC=10
```

---

