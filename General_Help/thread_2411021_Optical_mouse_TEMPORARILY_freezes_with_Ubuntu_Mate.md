---
title: "Optical mouse TEMPORARILY freezes with Ubuntu Mate 18.04"
date: 2019-01-23
forum: General Help
---

### Post by Jay_E on 2019-01-23
Greetings.

My mouse freezes when moving on the desktop.

Here is what syslog says:
```

Jan 23 12:50:52 pc-14 upowerd[2149]: unhandled action 'unbind' on /sys/devices/pci0000:00/0000:00:12.0/usb4/4-3/4-3:1.0/0003:192F:0416.0023
Jan 23 12:50:52 pc-14 upowerd[2149]: unhandled action 'unbind' on /sys/devices/pci0000:00/0000:00:12.0/usb4/4-3/4-3:1.0
Jan 23 12:50:52 pc-14 upowerd[2149]: unhandled action 'unbind' on /sys/devices/pci0000:00/0000:00:12.0/usb4/4-3
Jan 23 12:50:52 pc-14 kernel: [214721.146521] usb 4-3: new low-speed USB device number 43 using ohci-pci
Jan 23 12:50:53 pc-14 kernel: [214721.310521] usb 4-3: device descriptor read/64, error -62
Jan 23 12:50:53 pc-14 kernel: [214721.578514] usb 4-3: device descriptor read/64, error -62
Jan 23 12:50:53 pc-14 kernel: [214721.842515] usb 4-3: new low-speed USB device number 44 using ohci-pci
Jan 23 12:50:53 pc-14 kernel: [214722.036084] usb 4-3: New USB device found, idVendor=192f, idProduct=0416
Jan 23 12:50:53 pc-14 kernel: [214722.036087] usb 4-3: New USB device strings: Mfr=0, Product=2, SerialNumber=0
Jan 23 12:50:53 pc-14 kernel: [214722.036089] usb 4-3: Product: USB Optical Mouse
Jan 23 12:50:53 pc-14 kernel: [214722.043512] input: USB Optical Mouse as /devices/pci0000:00/0000:00:12.0/usb4/4-3/4-3:1.0/0003:192F:0416.0024/input/input53
Jan 23 12:50:53 pc-14 mtp-probe: checking bus 4, device 44: "/sys/devices/pci0000:00/0000:00:12.0/usb4/4-3"
Jan 23 12:50:53 pc-14 mtp-probe: bus: 4, device: 44 was not an MTP device
Jan 23 12:50:53 pc-14 kernel: [214722.102773] hid-generic 0003:192F:0416.0024: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:12.0-3/input0
Jan 23 12:50:53 pc-14 upowerd[2149]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:12.0/usb4/4-3/4-3:1.0/0003:192F:0416.0024
Jan 23 12:50:53 pc-14 upowerd[2149]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:12.0/usb4/4-3/4-3:1.0
Jan 23 12:50:53 pc-14 upowerd[2149]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:12.0/usb4/4-3
Jan 23 12:50:58 pc-14 kernel: [214726.442879] usb 4-3: reset low-speed USB device number 44 using ohci-pci
Jan 23 12:51:15 pc-14 kernel: [214743.842288] usb 4-3: reset low-speed USB device number 44 using ohci-pci
Jan 23 12:51:19 pc-14 kernel: [214747.596175] usb usb4-port3: disabled by hub (EMI?), re-enabling...
Jan 23 12:51:19 pc-14 kernel: [214747.596182] usb 4-3: USB disconnect, device number 44

```

The processor is:  AMD FX(tm)-8150 Eight-Core Processor
I am crunching work units with BOINC on 7 of the 8  processors.

I run a test of moving the mouse in a circle. It will freeze about every 5 seconds for a second or two; then continues.

The actual problem happens when I try to move between windows.
Th mouse freezes somewhere and the wait is longer.

I can reproduce the problem while not running BOINC and just the Ubuntu background processes running; still, problem happens.

With BOINC running I am using 2.5 GiB of 11.6 GiB of ram. there is no swapping at the moment;
so I don't think memory is the problem.

I do not know the limits/capabilities of a "low speed" usb device - the mouse. Is that speed a problem??


Should I borrow a different mouse from a neighbor and see if the problem still happens?

I am really interested in why the error happens and the cause of the messages logged into syslog.

THANKS in advance!!!

Jay

---

### Post by #&amp;thj^% on 2019-01-23
> **Jay_E said:**
> 
Should I borrow a different mouse from a neighbor and see if the problem still happens?


This is what I would do to be sure.

---

### Post by Jay_E on 2019-01-24
> **1fallen said:**
> This is what I would do to be sure.

Hey There!
   It was not the mouse. It was the settings.

system -> hardware -> Mouse

Settings WERE:
  POINTER SPEED:
       Acceleration: Slow ( selector was against left of slider scale.)
        Sensitivity: Low ( selector was against left of slider scale.)

Settings Changed: (PROBLEM GOES AWAY!!!)
  POINTER SPEED:
       Acceleration:  roughly 25% of the way between slow and fast.
        Sensitivity: roughly 25% of the way between low and high.


--Verification--
 Put sliders against left border; problem returned.
 Set to roughly 25% marks; Problem goes away.

Will write problem report tomorrow.

Jay

Thanks for you support!!

---

