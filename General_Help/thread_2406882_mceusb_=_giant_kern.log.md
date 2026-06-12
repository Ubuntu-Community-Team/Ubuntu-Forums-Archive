---
title: "mceusb = giant kern.log"
date: 2018-11-27
forum: General Help
---

### Post by Alexander_Lilljebj on 2018-11-27
Hi, 

Yesterday I noticed I was running out of space on my root partition. Finally found that my kern.log was 7.5Gb, filled with this error:

mceusb 2-1.4:1.0: [COLOR=#ff0000]Error:[/COLOR] urb status = -32 (RX HALT)

I've been googling like crazy, but I have not been able to find out why this is happening.

Any suggestions? 
Thanks

(Lubuntu 18.10 amd64)

---

### Post by TheFu on 2018-11-27
MCE - Machine Check Events

That often means hardware failure.  If related to USB, then I'd expect the issue is with:
* USB controller
* USB cable
* USB device

Watch all the logs for other issues nearby.  Google found this: [https://www.kernel.org/doc/html/v4.15/driver-api/usb/URB.html](https://www.kernel.org/doc/html/v4.15/driver-api/usb/URB.html)

---

### Post by Alexander_Lilljebj on 2018-11-28
Thank you so much for your reply. Will continue to monitor the logs for associated errors.

---

### Post by Holger_Gehrke on 2018-11-28
From 'modinfo mceusb':
```

filename:       /lib/modules/4.15.0-39-generic/kernel/drivers/media/rc/mceusb.ko
license:        GPL
author:         Jarod Wilson <jarod@redhat.com>
description:    Windows Media Center Ed. eHome Infrared Transceiver device driver
srcversion:     4F64E5B991D98D497DC33D7

```
An URB is an USB Request Block, a data structure used for communication between the USB stack and drivers for USB devices. This has a field 'status' which gets set to various values when the transfer has been completed. In your case the returned value is -32 (negative values are errors) meaning 'RX HALT'.

If you don't use a remote control with your machine, you could just blacklist the driver in a file in '/etc/modprobe.conf'.

Holger

---

### Post by Alexander_Lilljebj on 2019-01-05
Thanks again Holger!

We've had an unexpected death in the family, so as you can imagine, answering forum posts has been on the back burner.

Anyway, my error now shows:

mceusb 3-1:1.0: Error: urb status = -71

And I am in fact using an old MCE receiver on the computer displaying this error. It's mostly working, but the kern.log is still going crazy with this error.
And the only answer pertaining to this I've found, is this old one:
[https://ubuntuforums.org/showthread.php?t=2203116](https://ubuntuforums.org/showthread.php?t=2203116)
which sadly doesn't help me very much (I'm guessing mostly because of me being quite new to linux in general).

So any pointers would be greatly appreciated!

---

### Post by TheFu on 2019-01-05
That patch should have been integrated into the 4.x kernel line long ago.
I use an MCE device on my media center playback systems.  It is a $17 RC-6 remote from at least 10 yrs ago.

First, did you swap the USB cable out?
Is there a USB hub anywhere?  Remove it.  Hubs often introduce issues.
Have you tried the device on another computer?  Are there similar issues or not?  After all, an old MCE receiver could easily be broken.

I don't have any URB messages at all in my media playback systems logs. They run a 4.14.x kernel.

These are the only messages anywhere:
```
$ dmesg |grep -i mceusb
[    9.624952] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[    9.922693] mceusb 1-1.5:1.0: Registered Formosa21 eHome Infrared Transceiver with mce emulator interface version 1
[    9.922712] mceusb 1-1.5:1.0: 0 tx ports (0x0 cabled) and 1 rx sensors (0x1 active)
[    9.922943] usbcore: registered new interface driver mceusb
```

Of course, this all might have nothing to do with your situation. Just providing another data point for consideration.

---

### Post by Alexander_Lilljebj on 2019-01-05
> **TheFu said:**
> That patch should have been integrated into the 4.x kernel line long ago.
I use an MCE device on my media center playback systems.  It is a $17 RC-6 remote from at least 10 yrs ago.

First, did you swap the USB cable out?
Is there a USB hub anywhere?  Remove it.  Hubs often introduce issues.
Have you tried the device on another computer?  Are there similar issues or not?  After all, an old MCE receiver could easily be broken.

I don't have any URB messages at all in my media playback systems logs. They run a 4.14.x kernel.

These are the only messages anywhere:
```
$ dmesg |grep -i mceusb
[    9.624952] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[    9.922693] mceusb 1-1.5:1.0: Registered Formosa21 eHome Infrared Transceiver with mce emulator interface version 1
[    9.922712] mceusb 1-1.5:1.0: 0 tx ports (0x0 cabled) and 1 rx sensors (0x1 active)
[    9.922943] usbcore: registered new interface driver mceusb
```

Of course, this all might have nothing to do with your situation. Just providing another data point for consideration.

Thanks for your reply TheFu. 

Yeah, mine is around 13 yo as well. I believe I've switched the cable out, but that was a few years ago (so might be that, true). 

My computer running Lubuntu isn't very new either, around 5-6 years if I remember correctly, so might be something's beginning to give up there as well. 

The post was me trying to rule out a software error before starting to throw money at it (which I don't have&#128522;)

Edit, here's mine:

```
dmesg | grep -i mceusb[    6.552207] rc rc0: lirc_dev: driver mceusb registered at minor = 0, raw IR receiver, raw IR transmitter
[    6.752372] mceusb 3-1:1.0: long-range (0x1) receiver active
[    6.813134] mceusb 3-1:1.0: Registered SMK eHome Infrared Transceiver with mce emulator interface version 1
[    6.813146] mceusb 3-1:1.0: 2 tx ports (0x3 cabled) and 2 rx sensors (0x1 active)
[    6.813187] usbcore: registered new interface driver mceusb

```

And oh yeah, I'm not running lirc. I'm using this:
[https://github.com/clontarfx/kodi-rc6-mce-nolirc](https://github.com/clontarfx/kodi-rc6-mce-nolirc)

Might that be the problem?

---

### Post by TheFu on 2019-01-05
I use Kodi via OSMC on a set of raspberry pis for playback.  The driver sorta "just works" with the IR receiver at the end of a cheap USB 1.1 cable I had lying around 10-15 yrs ago when I first installed XBMC pre-Pi, pre-E-450, pre-Asus Eee. I've had that remote a very long time.

Have you tried plugging it into a different USB port - perhaps on a different channel?  Use **lsusb -t** to see the different u
BTW, I've asked a few questions above. Hard to help without any answers to eliminate some stuff.

---

### Post by Alexander_Lilljebj on 2019-01-06
> **TheFu said:**
> I use Kodi via OSMC on a set of raspberry pis for playback.  The driver sorta "just works" with the IR receiver at the end of a cheap USB 1.1 cable I had lying around 10-15 yrs ago when I first installed XBMC pre-Pi, pre-E-450, pre-Asus Eee. I've had that remote a very long time.

Have you tried plugging it into a different USB port - perhaps on a different channel?  Use **lsusb -t** to see the different u
BTW, I've asked a few questions above. Hard to help without any answers to eliminate some stuff.

Yeah, sorry about that. Had my son screaming in my ear for attention. 

No usb hub and I've tried switching ports to no avail.
I've been running Windows 7 on the same computer for the last few years and it worked then apart from losing connection maybe once every 14 days. And I'm afraid I don't have any other computers running linux at home, but I guess I can dual boot one to try it out that way. 

Thanks again for your patience.

Edit:
Just remembered that the computer crashes when on screensaver sometimes. When I turn on the screen everything is just stuck with artifacts. This happens maybe once in 14 days, and the computer is on around 14 hours a day every day. 
I've run memtests and get no errors, just for a few hours though.

Edit 2: 
It seems I'm getting this a few times a day as well:
```
kernel: [    1.341539] RAS: Correctable Errors collector initialized.


```

---

### Post by TheFu on 2019-01-06
lsusb -t?

I suspect it is simply a broken remote. $18 fixes that.

---

### Post by Alexander_Lilljebj on 2019-01-06
> **TheFu said:**
> lsusb -t?

I suspect it is simply a broken remote. $18 fixes that.

Apparently I can't read, so sorry that you've had to repeat yourself... 

lsusb -t:
```
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 480M
    |__ Port 2: Dev 3, If 0, Class=Vendor Specific Class, Driver=rtl8812au, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
        |__ Port 4: Dev 3, If 0, Class=Vendor Specific Class, Driver=mceusb, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M 
```

Did you mean remote or receiver? Because I'm using a Harmony 525 as remote(yeah I know, should have written that in the initial post).

---

