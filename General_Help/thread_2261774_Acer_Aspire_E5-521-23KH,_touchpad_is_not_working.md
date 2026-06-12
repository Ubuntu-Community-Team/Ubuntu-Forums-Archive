---
title: "Acer Aspire E5-521-23KH, touchpad is not working"
date: 2015-01-20
forum: General Help
---

### Post by Doug_Thomas on 2015-01-20
Solved!!
[COLOR=#000000]Ok, I finally got everything working and it ended up being a super easy fix. I updated my linux kernel from the update manager and voila! Touchpad is working and my graphics look way better. Hopefully this helps someone else.
[/COLOR]

So I just installed Ubuntu 14.04 on my laptop that was previously running windows 8.1. I have everything working except for the touchpad. All I know is that it should be a Synaptics touchpad. From what I can tell the Ubuntu doesn't even recognize it all? Wireless mouse works fine. So where do I start trying to get this thing working??

Acer Aspire E5-521-23KH
```

cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0


I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=4000 0 0


I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
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
B: KEY=10000000000000 0


I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 
B: PROP=0
B: EV=120013
B: KEY=10000 c020000000000 0 0 700f02000003 3802078f870f401 febfffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7


I: Bus=0003 Vendor=046d Product=c52b Version=0111
N: Name="Logitech Unifying Device. Wireless PID:401b"
P: Phys=usb-0000:00:12.0-1.2:1
S: Sysfs=/devices/pci0000:00/0000:00:12.0/usb1/1-1/1-1.2/1-1.2:1.2/0003:046D:C52B.0003/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=0
B: EV=17
B: KEY=ffff0000 0 0 0 0
B: REL=143
B: MSC=10


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HD-Audio Generic HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.1/sound/card0/input7
U: Uniq=
H: Handlers=event7 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HD-Audio Generic Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:14.2/sound/card1/input8
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=4


I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Acer WMI hotkeys"
P: Phys=wmi/input0
S: Sysfs=/devices/virtual/input/input9
U: Uniq=
H: Handlers=rfkill kbd event9 
B: PROP=0
B: EV=13
B: KEY=1c0000 0 0 0 0 1600800000c00 300000 0 0
B: MSC=10


I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Acer BMA150 accelerometer"
P: Phys=wmi/input1
S: Sysfs=/devices/virtual/input/input10
U: Uniq=
H: Handlers=event10 js0 
B: PROP=0
B: EV=9
B: ABS=7


I: Bus=0003 Vendor=06cb Product=2970 Version=0111
N: Name=" "
P: Phys=usb-0000:00:13.0-1.3/input0
S: Sysfs=/devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input11
U: Uniq=
H: Handlers=mouse1 event11 
B: PROP=1
B: EV=b
B: KEY=e520 10000 0 0 0 0
B: ABS=260800000000003


I: Bus=0003 Vendor=04f2 Product=b452 Version=2969
N: Name="HD WebCam"
P: Phys=usb-0000:00:12.0-1.4/button
S: Sysfs=/devices/pci0000:00/0000:00:12.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input13
U: Uniq=
H: Handlers=kbd event12 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

```

---

### Post by ajgreeny on 2015-01-21
Did the touchpad work in the live system when you were installing, or did you install without going to the live desktop?

It is always worth trying the live system first as it may point out potential problems such as you're experiencing.

---

### Post by Doug_Thomas on 2015-01-23
It never worked with the live CD

---

### Post by Pilot6 on 2015-01-23
Please give output of

dmesg | grep pnp
uname -a

---

### Post by Pilot6 on 2015-01-23
I can try to add usbid to the existing driver. It may work or may not.

---

### Post by Pilot6 on 2015-01-23
Now I looked at the code and 99% it won't work.
It is not supported yet. And it is hard to add support, not having the device.

But it may be supported thru hid. Which kernel do you have.

---

### Post by Doug_Thomas on 2015-01-25
doug@doug-Aspire-E5-521 ~ $ dmesg | grep pnp
[    0.412583] pnp: PnP ACPI init
[    0.413120] pnp 00:01: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.413197] pnp 00:02: [dma 4]
[    0.413239] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.413297] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.413383] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.413432] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.413519] pnp 00:06: Plug and Play ACPI device, IDs MSF0001 PNP0303 (active)
[    0.415324] pnp: PnP ACPI: found 9 devices
[    1.483619] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[  355.036507] dpm_run_callback(): pnp_bus_resume+0x0/0xa0 returns -19
[  834.176710] dpm_run_callback(): pnp_bus_resume+0x0/0xa0 returns -19
[14695.695507] dpm_run_callback(): pnp_bus_resume+0x0/0xa0 returns -19
[17165.327095] dpm_run_callback(): pnp_bus_resume+0x0/0xa0 returns -19
doug@doug-Aspire-E5-521 ~ $ uname -a
Linux doug-Aspire-E5-521 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
doug@doug-Aspire-E5-521 ~ $

---

### Post by Doug_Thomas on 2015-01-31
Ok, I finally got everything working and it ended up being a super easy fix.  I updated my linux kernel from the update manager and voila! Touchpad is working and my graphics look way better.  Hopefully this helps someone else.

---

