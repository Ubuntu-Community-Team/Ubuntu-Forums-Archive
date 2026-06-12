---
title: "Integrated webcam recently stopped working"
date: 2016-11-05
forum: General Help
---

### Post by jon-carmicheal on 2016-11-05
I've been using Ubuntu on my Dell Inspiron 14R for a long time now, but recently I have not been able to use the integrated webcam.  I've tried cheese, skype, and guvcview, but none of them can open the camera.  Usually I see the light next to the camera flicker on for a split second, and it does that a few times before stopping.  I'm hoping the hardware hasn't stopped working, and that it's something with the software.  I don't know that I have used it since reinstalling at the 16.04 version.  I've installed cheese and guvcview, which in the past has been all that's been required for me to get it working.  Now, when I reboot, I see that /dev/video0 exists.  If I run guvcview, /dev/video0 goes away, and /dev/video1 appears.  If I use cheese, /dev/video0 disappears, and never comes back (observed rather informally).  The following is the output in syslog while trying to run guvcview:

Nov  5 13:53:45 Linux-Lemur kernel: [54373.766822] usb 1-1.4: USB disconnect, device number 24
Nov  5 13:53:45 Linux-Lemur kernel: [54373.986105] usb 1-1.4: new high-speed USB device number 29 using ehci-pci
Nov  5 13:53:45 Linux-Lemur kernel: [54374.120654] usb 1-1.4: New USB device found, idVendor=0c45, idProduct=641d
Nov  5 13:53:45 Linux-Lemur kernel: [54374.120658] usb 1-1.4: New USB device strings: Mfr=2, Product=1, SerialNumber=0
Nov  5 13:53:45 Linux-Lemur kernel: [54374.120660] usb 1-1.4: Product: Laptop_Integrated_Webcam_1.3M
Nov  5 13:53:45 Linux-Lemur kernel: [54374.120662] usb 1-1.4: Manufacturer: CN0FJT7K724870AA0A03A01
Nov  5 13:53:45 Linux-Lemur kernel: [54374.123470] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (0c45:641d)
Nov  5 13:53:45 Linux-Lemur kernel: [54374.155455] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input21
Nov  5 13:49:31 Linux-Lemur gnome-session[2033]: ** (zeitgeist-datahub:2612): WARNING **: zeitgeist-datahub.vala:212: Error during inserting events: GDBus.Error:org.gnome.zeitgeist.EngineError.InvalidArgument: Incomplete event: interpretation, manifestation and actor are required
Nov  5 13:53:45 Linux-Lemur mtp-probe: checking bus 1, device 29: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4"
Nov  5 13:53:45 Linux-Lemur mtp-probe: bus: 1, device: 29 was not an MTP device


Does that help indicate anything that I might be able to fix?

---

