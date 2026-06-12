---
title: "Ubuntu 14.10 Multiple Problems Since I tried to help out the kernel team"
date: 2014-11-21
forum: General Help
---

### Post by 7-webmaster on 2014-11-21
No more mister nice guy.

For over two years, since Ubuntu 12.4 I have had a problem on my laptop that it would not reliably suspend when the lid was closed or resume when the lid was opened.  Typically the only recourse is the power button.  I have diligently submitted all of the Apport dumps, and the system has only marginally improved.  The driver support is advertised to be much better in kernel 3.16, so I upgraded to 14.10.  I observe that the system now suspends when I close the lid 100% of the time, and resumes 100% of the time when I open the lid.  Just one small problem:  The stupid driver doesn't turn the back-light on my LED screen on, so it doesn't do me much good that the system is actually operating since I cannot do anything with it except reboot, and since the system has actually resumed it is not really safe to hit the power button, a single finger stroke, so I now have to Alt-PrtScrn-RSEIUB!  I submitted a report and I got back a flurry of responses.  One person suggested I upgrade the BIOS.  Only one little problem there: the manufacturer only permits updating the BIOS from Windoze!  So I rebooted, performed the upgrade, and then tried again.  No change in behavior.  Then I was asked to see if the problem was already fixed on kernel 3.18.  Big mistake!  My system hasn't worked since.  I even reformatted the drive and installed from the DVD and the d.....d system won't run properly.

1) Every version of Ubuntu I have used for many years had no problem using the display.  Now Ubuntu insists that the ONLY resolution it can use is 1024:768 (3:4) instead of 1600:900!  So I have half of the usable space on my screen, and everything is stretched because, of course, the screen is actually 9:16!  I have tried manually reinstalling the Xorg driver.  I have tried the fglrx driver.  I have tried reinstalling the whole damn operating system from scratch!  Nothing works.
2) Having in desperation reinstalled the whole operating system from the DVD of course I have to restore all of the files that I diligently copied to a USB attached hard-drive.  Only now the system refuses to mount the drive.  dmesg shows the drive being plugged in, but it never appears under /media.
```

[  273.093992] usb 8-2: new high-speed USB device number 3 using xhci_hcd
[  273.224888] usb 8-2: New USB device found, idVendor=13fd, idProduct=1840
[  273.224901] usb 8-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  273.224908] usb 8-2: Product: External        
[  273.224913] usb 8-2: Manufacturer: Generic 
[  273.224917] usb 8-2: SerialNumber: 355643334B464B4520202020

```

And the device shows up in the output of lsusb:

Bus 008 Device 004: ID 13fd:1840 Initio Corporation INIC-1608 SATA bridge

but there is nothing in /media/<userid> so I cannot restore all of those saved files!

I have been running Ubuntu for over 7 years, ever since Gutsy Gibbon, and I have never faced so many problems.

If reinstalling the operating system from scratch doesn't clear this up, what am I supposed to do to get my computer working again?

---

### Post by 7-webmaster on 2014-11-22
I tucked my computer into bed last night.  This morning I woke it up, which still requires Alt-PrtScrn-RSEIUB, installed kernel 3.16.24 and the screen resolution problem was resolved.  Also the USB attached hard drive mounted.  So all I have left is the problem with the gd GD which still refuses to turn the back-light on the display.

---

