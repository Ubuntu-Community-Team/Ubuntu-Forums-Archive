---
title: "USB Not working correctly for device"
date: 2006-07-10
forum: General Help
---

### Post by superm1 on 2006-07-10
Now I'm almost exclusively linux (my motorola wr850g, my amd64 desktop, my laptop, 2 mythtv servers, 2 mythtv frontends, my ipod, and even my gamecube boots up a linux kernel occasionally)

I have one thing keeping me from wiping the windows partition.  I have a loading utility for my cell phone that is only available in windows, and a flashing utility for my gamecube mod chip.  I don't do either of these very much, I figured I'm better wiping the dual boot and installing into QEMU or vmware.  I tried to use QEMU, but the speed was unbareably slow (even with kqemu), and when I finally got in, the USB device wasn't identifying correctly in Windows "Unknown Device".  Normally it is some sort of Generic HID device not needing drivers in windows.

I realized the USB support in QEMU isn't exactly mature yet.  So i grabbed the latest vmware-player & generated a VMX from easyvmx.com.  I installed windows in here as well, and the performance was much better (but I will need more RAM if I will keep using it).  Now I get in, and again the USB is showing up the same way.  "Unknown Device" in windows.  Even worse, if I unplug and and plug it back in, until the device settles, the virtual machine freezes.


So now I realize that there must be going on funky with linux and this modchip.  Sure enough, its timing out when initializing, but linux is eventually picking it up as a HID device.

```
Jul  9 16:05:48 localhost kernel: [1014373.133718] usb 4-2: new full speed USB device using uhci_hcd and address 14
Jul  9 16:05:59 localhost kernel: [1014383.274274] drivers/usb/input/hid-core.c: timeout initializing reports
Jul  9 16:05:59 localhost kernel: [1014383.274278]
Jul  9 16:05:59 localhost kernel: [1014383.274334] hiddev96: USB HID v1.00 Device [QooB Team QOOB Chip Pro] on usb-0000:00:1d.3-2
```


Could someone think of why things aren't working right here?  Or possibly even suggest another solution to this problem?  I'd much prefer a small windows install to only fire up in vmware every so often when I want to flash the cube or put some ring tones on rather then reboot.

---

