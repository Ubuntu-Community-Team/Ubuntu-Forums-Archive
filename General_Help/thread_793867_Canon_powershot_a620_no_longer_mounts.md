---
title: "Canon powershot a620 no longer mounts"
date: 2008-05-14
forum: General Help
---

### Post by Aled Y Cymro on 2008-05-14
It worked in 7.10, but now it doesn't even recognise it. Normally, you'd just turn it on, and flick a switch on the camera, but now that doesn't show the camera's folder.

Is there a way of manually mounting the camera?

---

### Post by Aled Y Cymro on 2008-05-23
Hate to bump a thread and all, but this is quite vital for me.

---

### Post by BandD on 2008-05-23
Have you tried using F-Spot or gtkam (in the repos)?  

I really like gtkam, it works wonders for my Canon 30D SLR.  The number of cameras that it supports is quite impressive.

---

### Post by Chriis on 2008-05-28
Canon powershot S3 no longer mounts here, was ok in Gutsy.

No solutions yet, need help please :-)

Chriis

---

### Post by BandD on 2008-05-28
With the camera plugged in and on and you post the results of:

```
lsusb
```

and just after you plug in the camera and turn it on:

```
dmesg | tail
```

The first will list all usb devices detected by your system and the second will show us if there is a record by the system of your camera being plugged in.  It'll be easier to know where to go from there.

---

### Post by LeBurt on 2008-06-02
I'm having the same problem with a PowerShot A530. Nothing happens when I plug it in and I can't launch F-Spot manually.

lsusb says:
Bus 006 Device 009: ID 04a9:3126 Canon, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 041e:401d Creative Technology, Ltd WebCam NX Ultra
Bus 001 Device 001: ID 0000:0000  


dmesg | tail says:
[71023.260323] UDP: bad checksum. From 60.191.19.46:54901 to 70.82.96.212:4672 ulen 46
[71180.868536] atl1 0000:02:00.0: hw csum wrong, pkt_flag:e00, err_flag:80
[71180.868548] UDP: bad checksum. From 122.224.188.59:39263 to 70.82.96.212:4672 ulen 46
[71998.767248] atl1 0000:02:00.0: hw csum wrong, pkt_flag:e00, err_flag:80
[71998.767260] UDP: bad checksum. From 122.224.188.59:40595 to 70.82.96.212:4672 ulen 46
[73083.896242] usb 6-7: new high speed USB device using ehci_hcd and address 9
[73083.965215] usb 6-7: configuration #1 chosen from 1 choice
[73092.110657] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[73093.621482] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[73095.136841] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?

From what I can see, the camera gets recognized at least on the USB level. Any ideas on how can I troubleshoot this one notch further?

---

### Post by BandD on 2008-06-02
Have you tried using gtkam (you can install it via synaptic)?  

Many people seem to be having problems with camera on Hardy.  Check out this bug report, and maybe add yourself to it:
[URL="https://bugs.launchpad.net/ubuntu/+bug/215234"]
https://bugs.launchpad.net/ubuntu/+bug/215234[/URL]

Let me know if gtkam works or not.

---

### Post by RomanIvanov on 2008-12-12
gtkam does not help. It could not detect my PowerShot A620. I even tried to select from list and select usb - does not work. My system is Xubuntu 8.10. Any ideas?

FYI:
romani@romani-laptop:~$ lsusb
Bus 007 Device 005: ID 04a9:30fc Canon, Inc. PowerShot A620 (PTP mode)

---

### Post by fragos on 2008-12-13
My Canon S3 IS works fine with Ubuntu 8.10, even turning the camera on when the cord is connected. In Gnome the camera can mount with a photo application or in Nautilus as a card reader. This would be configurable in preferences. I'm not a Xubuntu user. Try opening "f-spot" in a terminal window. You should see error messages if the application has trouble starting. If you can't see your camera is "lsusb" you have a hardware issue. Your system can recognize any USB device even if the driver necessary to use it isn't available.

---

### Post by RomanIvanov on 2008-12-14
Thanks a lot for "f-spot", I installed it and it works like a charm!! 

I even checked gtkam (after installation of f-spot) - it still could not connect to my cam.

---

