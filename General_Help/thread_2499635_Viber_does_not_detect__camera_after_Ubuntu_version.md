---
title: "Viber does not detect  camera after Ubuntu version upgrade"
date: 2024-08-05
forum: General Help
---

### Post by Andreyshel on 2024-08-05
Viber does not detect my camera while Google meet and Cheese work just fine.
This problem started after upgrade( reinstall  with /home remaining not formatted) from Ubuntu 22.04 to 24.04.
Viber 21.8.0.11(Installed via official deb, but have tried appimage version as well with no effect)
Kernel 6.8.0-39-generic
Camera: Bus 001 Device 003: ID 046d:082d Logitech, Inc. HD Pro Webcam C920


I wanted to start lshw -c USB  to show information about camera driver but this command hangs on Network interfaces.

Thank you for any ideas.

---

### Post by TheFu on 2024-08-05
X11 or Wayland?  In theory, that shouldn't matter for a webcam.

My C920 died after 8 yrs and I haven't replaced it.  When I plug it in via USB, I see this:
```
$ dmesg -w
[2598529.357916] usb 1-2: new high-speed USB device number 77 using xhci_hcd
[2598531.866608] usb 1-2: New USB device found, idVendor=046d, idProduct=082d, bcdDevice= 0.11
[2598531.866614] usb 1-2: New USB device strings: Mfr=0, Product=2, SerialNumber=1
[2598531.866617] usb 1-2: Product: HD Pro Webcam C920
[2598531.866620] usb 1-2: SerialNumber: xxxxxxxxxx
[2598532.218801] videodev: Linux video capture interface: v2.00
[2598532.237239] usb 1-2: Found UVC 1.00 device HD Pro Webcam C920 (046d:082d)
[2598532.302963] input: HD Pro Webcam C920 as /devices/pci0000:00/0000:00:02.1/0000:01:00.0/usb1/1-2/1-2:1.0/input/input39
[2598532.303052] usbcore: registered new interface driver uvcvideo
```


Do you see something similar?  There should be 2 devices - 1 for video and 1 for the microphone.  The video device gets listed in /dev/video* - I have a few video devices there, so don't know which is which.  I have a Magewell capture card too which is different than a webcam but shows up as a /dev/video* device.

```
$ lsusb
...
Bus 001 Device 057: ID 046d:c341 Logitech, Inc. HD Pro Webcam C920
Bus 001 Device 077: ID 046d:082d Logitech, Inc. HD Pro Webcam C920
...
```

I don't use viber.  I do have OBS loaded and that is working with the camera and X11.  Yep. Just tested.  Though I don't have 24.04. Too new for my needs.  I'm still on 20.04.  Stability is more important to me than "new".  I will be using X11 for as long as possible. Wayland breaks a number of my workflows, unfortunately. Wayland closes some security holes in X11 that are needed for those workflows to actually work.  I don't know if Wayland or X11 matter at all. Just something that could break video handling and it is an easy thing to switch for a quick test.

---

### Post by Andreyshel on 2024-08-06
> X11 or Wayland? In theory, that shouldn't matter for a webcam.
Have tried both without an effect.
> [COLOR=#000000]Do you see something similar? There should be 2 devices - 1 for video and 1 for the microphone.[/COLOR]
Interesting. In lsusb output there  is only one. Dmesg output is simular.  But the same is the case for 22.04.3 livecd. So it should not be a problem

---

### Post by Andreyshel on 2024-08-25
[https://github.com/flathub/com.viber.Viber/issues/88](https://github.com/flathub/com.viber.Viber/issues/88)

Believe answer of wooque user is the solution. Tried to implement but simply too many packages need to be installed manually.

Downgrade to 22.04 is almost more reasonable in this case.

---

### Post by hifron on 2024-08-26
try in /etc/modules-load.d/webcam.conf

uvcvideo

maybe also v4l2loopback because some softs requires that. maybe you need other drivers...

---

