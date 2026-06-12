---
title: "Unix command to check USB mouse"
date: 2008-04-24
forum: General Help
---

### Post by satimis on 2008-04-24
Hi folks,


I have an USB mouse without label.  What command shall I run to check whether it is 1.0 OR 2.0 version.

TIA


B.R.
satimis

---

### Post by kpkeerthi on 2008-04-24
Try
```
sudo lsusb -v
```

---

### Post by satimis on 2008-04-24
> **kpkeerthi said:**
> Try
```
sudo lsusb -v
```
Thanks for your advice.

There is an lengthy output.  Where shall I look at?

```

Device Descriptor:
  bLength           18
  bDescriptor Type  1
  bcdUSB            2.00
.....

```
Is it USB 2.0 ?


B.R.
satimis

---

### Post by kpkeerthi on 2008-04-24
Oops.. pipe it with **less** as in 
```
sudo lsusb -v | less
```
or better yet, send the output to a file
```
sudo lsusb -v > ~/usb-devices.txt
```

And yes, bcdUSB should tell you the USB version supported by the device. See [http://www.beyondlogic.org/usbnutshell/usb5.htm](http://www.beyondlogic.org/usbnutshell/usb5.htm)

---

### Post by warp99 on 2008-04-24
> **satimis said:**
> Hi folks,


I have an USB mouse without label.  What command shall I run to check whether it is 1.0 OR 2.0 version.

TIA


B.R.
satimis
```
cat /proc/bus/input/devices |more 
```

The first line will give the version information.

---

### Post by satimis on 2008-04-24
> **warp99 said:**
> ```
cat /proc/bus/input/devices |more 
```

The first line will give the version information.
Hi warp99,


Something I can't resolve.


The box is running a MS Wireless Laser mouse.  I unplug the USB Receiver.  Plugin the unlabeled USB Optical Mouse.


$ cat /proc/bus/input/devices | more```

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
H: Handlers=mouse0 ts0 event0 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3
.....

```


Unplug the USB Optical Mouse.  Plugin an USB Laser mouse.


$ cat /proc/bus/input/devices | more```

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
H: Handlers=mouse0 ts0 event0 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3
....
....

```


They look the same


B.R.
satimis

---

