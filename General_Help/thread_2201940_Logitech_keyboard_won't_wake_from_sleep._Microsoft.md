---
title: "Logitech keyboard won't wake from sleep. Microsoft Keyboard will"
date: 2014-01-26
forum: General Help
---

### Post by steveearle86 on 2014-01-26
Hi,
I am having a problem waking from sleep with a keyboard on Ubuntu 13.10. I have two usb ports at the front of my computer.

The keyboard I am using is this one 
[http://www.logitech.com/en-gb/product/wireless-touch-keyboard-k400r?wt.ac=ps%7C11080%7Ck400wh%7Chp](http://www.logitech.com/en-gb/product/wireless-touch-keyboard-k400r?wt.ac=ps%7C11080%7Ck400wh%7Chp)

and it will not wake from sleep with the receiver in either USB port. This keyboard will wake a Windows 7 machine I have from sleep OK.

I have also tried another keyboard I have:
[http://www.microsoft.com/hardware/en-gb/p/arc-keyboard](http://www.microsoft.com/hardware/en-gb/p/arc-keyboard)

which will wake the PC fine, no problems from either USB port. It also wakes the Windows 7 machine.

It seems there may be some sort of compatibility issue between the Logitech and Ubuntu.

Here is my lsusb (both keyboards plugged in)

```

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 005: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Here is cat /proc/acpi/wakeup
```

SBAZ      S4    *disabled  pci:0000:00:14.2
P0PC      S4    *disabled  pci:0000:00:14.4
GEC      S4    *disabled
UHC1      S4    *enabled   pci:0000:00:12.0
UHC2      S4    *enabled   pci:0000:00:12.2
USB3      S4    *enabled   pci:0000:00:13.0
UHC4      S4    *enabled   pci:0000:00:13.2
USB5      S4    *enabled   pci:0000:00:16.0
UHC6      S4    *enabled   pci:0000:00:16.2
UHC7      S4    *enabled   pci:0000:00:14.5
PE20      S4    *disabled  pci:0000:00:15.0
GBE      S4    *disabled
PE21      S4    *disabled
PE22      S4    *disabled
PE23      S4    *disabled
PWRB      S3    *enabled 

```

Does any one have any ideas how I might get this to work?
Thanks

---

### Post by bc.haynes on 2014-01-26
I am just a dumb redneck, but it seems that having two wireless keyboards plugged in at the same time would confuse the poor computer. Also, why not just use the MS keyboard if the LogiTech doesn't work? Ya'see, some of us is computer saavy. I know what spam is; I have it for breakfast twice a week. And I can download. Ever'body knows thats what you go to the outhouse for. 

[center][color=blue]Have a Great Day!![/color][/center]

---

### Post by martincannell503g on 2014-01-26
Its an ACPI problem.  In computing, the Advanced Configuration and Power Interface (ACPI) specification provides an open standard for device configuration and power management by an operating system.  That just means some computers don't know when to go sleep or wake up again on their own.  IRQ's are also effected.  You can generally work out what has happened by the way your machine behaves, Are all and everything suspended when ubuntu suspends or can something wake it, does the power suspend button wake it,  have you all kernel modules/drivers installed. ?  IRQ's  looking to wake ... make a lot on non-wakes (eg perminently looking for the never to be), and suspend to ram and big snooze [untilI BIOS setting] all and often leave no senario with which to wake.

Grub boot options often overide standards,  See  [ https://help.ubuntu.com/community/BootOptions]("http://help.ubuntu.com/community/BootOptions")  for ubuntu's ACPI overides.

---

### Post by bc.haynes on 2014-01-27
Thank you for the explanation and the link-it was informative. Now I know how to do **nomodeset**.

---

### Post by steveearle86 on 2014-01-28
> **bc.haynes said:**
> having two wireless keyboards plugged in at the same time would confuse the poor computer. Also, why not just use the MS keyboard if the LogiTech doesn't work?

I only have both plugged in for troubleshooting this problem. The behaviour for each keyboard is the same whether both are plugged in at the same time or not. This computer is a HTPC and the logitech keyboard has a tracker pad also. The other is just a keyboard

> [COLOR=#000000]Are all and everything suspended when ubuntu suspends or can something wake it, does the power suspend button wake it, have you all kernel modules/drivers installed. ? [/COLOR][COLOR=#000000]
[/COLOR]
The microsoft keyboard can wake as can the power button the front of the case
Neither the keyboard or the touchpad on the Logitech keyboard can wake the pc.
I have never installed any drivers for the keyboard It just worked straight from plugging in. Barring this issue of course

---

### Post by steveearle86 on 2014-01-28
Goin back to my original cat proc/acpi/wakeup  entry, PWRB is the only one that is S3. The USBs are S4. Could this be part of the problem?

---

### Post by steveearle86 on 2014-01-28
I have fixed it!

open
```
sudo nano /etc/udev/rules.d/90-keyboardwakeup.rules
```

add the code
```
SUBSYSTEM=="usb", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c52b" RUN+="/bin/sh -c 'echo enabled > /sys$env{DEVPATH}/../power/wakeup'"
```

the idVender and idProduct value are from the keyboard's entry in the lsusb table

---

### Post by sd12 on 2014-08-04
Thank you. This worked for me

---

