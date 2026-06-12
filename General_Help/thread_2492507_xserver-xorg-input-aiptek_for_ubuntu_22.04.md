---
title: "xserver-xorg-input-aiptek for ubuntu 22.04 ?"
date: 2023-11-13
forum: General Help
---

### Post by grey1beard on 2023-11-13
Trying to  *sudo apt-get install xserver-xorg-input-aiptek* , but get *Unable to locate package xserver-xorg-input-aiptek* on Terminal, after updating apt-get.
Any advice most welcome.
John

---

### Post by MAFoElffen on 2023-11-13
The last build of that package was for Bionic (18.04). No longer in the repo's.

---

### Post by grey1beard on 2023-11-14
Does that mean I can only access it if I was running 18.04 ?
My grasp of 'tech' is tenuous, to say the least !
John
EDIT Just discovered I was having the same problem in 2021, when I was trying to use it in 20.04 !
Didn't find a solution then, either.

---

### Post by MAFoElffen on 2023-11-14
What does this say:
```

sudo lspci -nnk | grep -v 'DeviceName' | grep -A3 -E 'VGA|Display|3D'
sudo lshw -C video | grep -E 'product|driver'

```
Maybe there is another driver that it will work with it...

---

### Post by Holger_Gehrke on 2023-11-14
Some minimum support for Aiptek graphics tablets is available in the kernel through a module named '/usr/lib/modules/{KERNEL_VERSION}-generic/kernel/drivers/input/tablet/aiptek.ko'. As far as I can tell this produces a device file somewhere in '/dev/input/'. There's a project page for the X driver and an application for setting the tablet up on sourceforge ( [https://aiptektablet.sourceforge.net/](https://aiptektablet.sourceforge.net/) ) but that hasn't been updated in 10 years ...

Holger

---

### Post by grey1beard on 2023-11-14
As requested -
> sudo lspci -nnk | grep -v 'DeviceName' | grep -A3 -E 'VGA|Display|3D'
[sudo] password for john: 
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
	Subsystem: Hewlett-Packard Company Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [103c:18e7]
	Kernel driver in use: i915
	Kernel modules: i915
john@john-HP-ProDesk-600-G1-SFF:~$ sudo lshw -C video | grep -E 'product|driver'
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       configuration: depth=32 driver=i915 latency=0 resolution=1360,768

---

### Post by grey1beard on 2023-11-14
Thanks Holger.
I've drilled down your first thought, and reached 0 byte files in /dev/input, > /dev/input/by-id/usb-AIPTEK_International_Inc._USB_Tablet_Series_Version_1.04-event-mouse.

I've previously found the project page you mentioned, but not sure how to follow that up !
John

---

### Post by grey1beard on 2023-11-14
I'm getting basic use out of the tablet, in that it allows me to trace a line drawing that I've made, via the tablet/pen, into inkscape.

The problem is that the X dimension is reported ~3 times bigger than the original, and the Y dimension ~2 times bigger.

If I can't resolve this, I shall scale the final drawing in inkscape, though obviously getting the tablet sizing correctly is preferable.
John

---

### Post by Holger_Gehrke on 2023-11-14
> **grey1beard said:**
> Thanks Holger.
I've drilled down your first thought, and reached 0 byte files in /dev/input, .

I've previously found the project page you mentioned, but not sure how to follow that up !
John

The ones in by-id are only links to /dev/input/event*. Those are device files, meaning they aren't "real" files at all but a way to access a device as if it were a file. The settings for the device should be in pseudo-files in /sys/bus/usb/drivers/aiptek. The various files in there and the meaning of their content and whether or not you can write to them can be found at [https://aiptektablet.sourceforge.net/kernel.html](https://aiptektablet.sourceforge.net/kernel.html)

Holger

---

### Post by grey1beard on 2023-11-14
Thanks. More reading to do !
Just followed your link. I think it might do my head in, but I'll try !

---

### Post by MAFoElffen on 2023-11-14
These drivers are in the current kernel: 
```

mafoelffen@Mikes-ThinkPad-T520:~/Downloads/ISO$ find / -name *AIPTEK* 2>/dev/null
/usr/src/linux-headers-6.2.0-36-generic/include/config/TABLET_USB_AIPTEK
/usr/src/linux-headers-5.15.0-58-generic/include/config/TABLET_USB_AIPTEK
/usr/src/linux-headers-6.2.0-33-generic/include/config/TABLET_USB_AIPTEK
/usr/src/linux-headers-5.15.0-88-generic/include/config/TABLET_USB_AIPTEK

```

---

### Post by grey1beard on 2023-11-15
*/usr/src/linux-headers-6.2.0-36-generic/include/config/TABLET_USB_AIPTEK* is present in the *Computer* location, but shows with 0 bytes.
What should my next step be ?
John

---

### Post by grey1beard on 2023-11-17
I think it's time to give up.
I've been beating my head against the wall too long, so thanks for all the fish.
John

---

