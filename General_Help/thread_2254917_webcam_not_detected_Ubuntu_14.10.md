---
title: "webcam not detected Ubuntu 14.10"
date: 2014-11-30
forum: General Help
---

### Post by Dragonbite on 2014-11-30
I have a Microsoft Corp. LifeCam NX-6000 webcam that has worked in previous version of Ubuntu (and other distributions) and in 14.10 I am being told "No device detected" when I try Cheese or Skype.
```
drew@Unicorn:~$ lsusb
Bus 002 Device 003: ID 045e:00f8 Microsoft Corp. LifeCam NX-6000
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I haven't had a problem like this in Ubuntu since like 2010 (basically, for a long, long time) and other distributions have detected it as well.  What can I do to get it detected?

---

### Post by carl4926 on 2014-11-30
Have you checked the behaviour in any of the older kernel option from the grub menu?
lsusb is showing the device

---

### Post by Dragonbite on 2014-12-06
There is only one older kernel and it doesn't show up with that one either.

The 14.10 installation is a clean installation, rather than an update from 14.04 or earlier so I don't have older kernels than 3.16 (I think that's it)..

---

### Post by llamabr on 2014-12-06
What do you get from dmesg when you plug the thing in?

---

### Post by Dragonbite on 2014-12-07
> **llamabr said:**
> What do you get from dmesg when you plug the thing in?

The following code is what was in dmesg after plugging in the webcam:
```

[ 2109.276064] [drm] HPD interrupt storm detected on connector HDMI-A-1: switching from hotplug detection to polling
[ 2156.076075] usb 2-1: new high-speed USB device number 2 using ehci-pci
[ 2156.212294] usb 2-1: New USB device found, idVendor=045e, idProduct=00f8
[ 2156.212301] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 2156.212307] usb 2-1: Product: Microsoft® LifeCam NX-6000
[ 2156.212311] usb 2-1: Manufacturer: Microsoft
[ 2156.248865] media: Linux media interface: v0.10
[ 2156.266434] Linux video capture interface: v2.00
[ 2156.289201] usb 2-1: 3:1 : sample bitwidth 24 in over sample bytes 2
[ 2156.290165] usb 2-1: 3:1: cannot get freq at ep 0x84
[ 2156.298637] usbcore: registered new interface driver snd-usb-audio
[ 2156.304134] uvcvideo: Found UVC 1.00 device Microsoft® LifeCam NX-6000 (045e:00f8)
[ 2156.309051] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[ 2156.310866] input: Microsoft® LifeCam NX-6000 as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0/input/input10
[ 2156.310987] usbcore: registered new interface driver uvcvideo
[ 2156.310990] USB Video Class driver (1.1.1)
[ 2156.819344] usb 2-1: 3:1: cannot get freq at ep 0x84
[ 2156.820481] usb 2-1: 3:1: cannot get freq at ep 0x84
[ 2156.836848] usb 2-1: 3:1: cannot get freq at ep 0x84
[ 2156.837593] usb 2-1: 3:1: cannot get freq at ep 0x84

```

The lines with ```
usb 2-1: 3:1: cannot get freq at ep 0x84
``` are in red in the terminal.

---

### Post by llamabr on 2014-12-07
I wonder if this is a problem with the UVC driver.  have a look at this thread:

[http://askubuntu.com/questions/393789/how-do-i-get-my-lifecam-vx-7000-working-on-ubuntu-13-10](http://askubuntu.com/questions/393789/how-do-i-get-my-lifecam-vx-7000-working-on-ubuntu-13-10)

and report back.

---

### Post by Dragonbite on 2014-12-08
> **llamabr said:**
> I wonder if this is a problem with the UVC driver.  have a look at this thread:

[http://askubuntu.com/questions/393789/how-do-i-get-my-lifecam-vx-7000-working-on-ubuntu-13-10](http://askubuntu.com/questions/393789/how-do-i-get-my-lifecam-vx-7000-working-on-ubuntu-13-10)

and report back.

The link listed 3 programs to install[LIST=1]
[*]libv4l-0
[*]libv4l-dev 
[*]guvcview
[/LIST]

The **libv4l-0** was already installed, so I installed the other 2 and that didn't make any difference. Even after rebooting (just in case).  I didn't have the chance to look at *dmesg* to see if the message changed, yet.

I also hadn't tried the linked conversation from the first one ([http://forums.linuxmint.com/viewtopic.php?f=49&t=170425](http://forums.linuxmint.com/viewtopic.php?f=49&t=170425)) yet so that is my next step.

---

### Post by llamabr on 2014-12-08
> **Dragonbite said:**
> I didn't have the chance to look at *dmesg* to see if the message changed, yet.

I also hadn't tried the linked conversation from the first one ([http://forums.linuxmint.com/viewtopic.php?f=49&t=170425](http://forums.linuxmint.com/viewtopic.php?f=49&t=170425)) yet so that is my next step.

Let us know what happened, particularly with dmesg.  My idea was that it's loading the wrong driver when you plug it in, so dmesg will reveal what it's doing.

---

