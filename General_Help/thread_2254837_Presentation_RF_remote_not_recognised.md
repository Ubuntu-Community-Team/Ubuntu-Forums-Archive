---
title: "Presentation RF remote not recognised"
date: 2014-11-30
forum: General Help
---

### Post by PhartSmellah on 2014-11-30
Hi all,

I've really been searching far and wide for a solution, but haven't come up with anything.
Hoping someone here will have some insight in the matter.

I've recently bought a generic (=cheap) **RF remote for presentations**. It doesn't work when connected to Ubuntu.
I tried connecting it to a Windows computer - still no luck. At this point I was sure its a faulty controller.
Then I plugged it into a Mac - and it worked. Maybe someone can help debug the behavior on the Mac and realize what's missing from my Ubuntu?

Here's what happens once the receiver is plugged in.
(Ubuntu 14.04 and Mac 10.10.1)

**On the Ubuntu:**
```

$ dmesg
...
[68297.924641] usb 2-1.1: new low-speed USB device number 21 using ehci-pci
[68298.037569] usb 2-1.1: New USB device found, idVendor=0c45, idProduct=3072
[68298.037577] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[68298.037580] usb 2-1.1: Product: USB Device
[68298.037583] usb 2-1.1: Manufacturer: SONiX
[68298.041258] input: SONiX USB Device as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.1/2-1.1:1.0/input/input37
[68298.041491] hid-generic 0003:0C45:3072.001C: input,hidraw3: USB HID v1.10 Keyboard [SONiX USB Device] on usb-0000:00:1d.7-1.1/input0

$ lsusb
...
Bus 002 Device 021: ID 0c45:3072 Microdia

$ cat /proc/bus/input/devices
...
I: Bus=0003 Vendor=0c45 Product=3072 Version=0110
N: Name="SONiX USB Device"
P: Phys=usb-0000:00:1d.7-1.1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.1/2-1.1:1.0/input/input37
U: Uniq=
H: Handlers=sysrq kbd event13 
B: PROP=0
B: EV=120013
B: KEY=80000000000000 e0b0ffdf01cfffff fffffffffffffffe
B: MSC=10
B: LED=1f

```

Trying *showkey* and *xev* - the console detects keyboard presses but no clicks on the remote's buttons.

**On the Mac:** 
When I plugged it in, a "configure/identify new keyboard" window popped up. I closed it.
I don't know how to reproduce all these printouts on a Mac... this is the best I came up with.
```

$ system_profiler SPUSBDataType
...
[FONT=arial]USB Device:[/FONT]
[FONT=arial]          Product ID: 0x3072[/FONT]
[FONT=arial]          Vendor ID: 0x0c45  (Sonix Technology Co., Ltd.)[/FONT]
[FONT=arial]          Version: 0.01[/FONT]
[FONT=arial]          Speed: Up to 1.5 Mb/sec[/FONT]
[FONT=arial]          Manufacturer: SONiX[/FONT]
[FONT=arial]          Location ID: 0x04100000 / 4[/FONT]
[FONT=arial]          Current Available (mA): 500[/FONT]
[FONT=arial]          Current Required (mA): 100[/FONT]


```

Am I missing a library of some kind?
Do you think [this solution]("http://linuxhifi.wordpress.com/2012/07/14/using-an-rf-remote-control-with-lirc/") might apply here? Couldn't find atilibusb in the official repos. Also, not that comfortable with that syntax...
Can someone guide me in debugging this further?

Thanks

---

### Post by PhartSmellah on 2015-02-03
Bump.
Hoping for a tiny lead here to guide me to a possible solution...

---

