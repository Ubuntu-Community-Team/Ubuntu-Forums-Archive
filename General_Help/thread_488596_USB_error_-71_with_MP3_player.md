---
title: "USB error -71 with MP3 player"
date: 2007-06-30
forum: General Help
---

### Post by oldHat on 2007-06-30
[FONT="Courier New"]I'm using Dapper on an Intel system.  I'm having trouble connecting my MP3 player(Sapphire Ivory) via USB.  Over and over, I get "error -71", then a retry.

dmesg shows this.

[17229137.372000] usb 4-1: new full speed USB device using uhci_hcd and address 2
[17229142.444000] usb 4-1: can't set config #1, error -71
[17229143.924000] usb 4-1: new full speed USB device using uhci_hcd and address 4
[17229148.988000] usb 4-1: can't set config #1, error -71
[17229150.476000] usb 4-1: new full speed USB device using uhci_hcd and address 6
[17229155.540000] usb 4-1: can't set config #1, error -71
[17229157.028000] usb 4-1: new full speed USB device using uhci_hcd and address 8
[17229162.092000] usb 4-1: can't set config #1, error -71
[17229163.584000] usb 4-1: new full speed USB device using uhci_hcd and address 10
[17229168.660000] usb 4-1: can't set config #1, error -71

"lsusb" does not list this device, even though it is plugged in.

Here's what "lsmod" says:

lsmod|grep usb
usb_storage            79648  1
usbhid                 42752  0
usbcore               139172  6 usb_storage,ndiswrapper,usbhid,uhci_hcd,ehci_hcd
scsi_mod              146088  4 usb_storage,sg,sd_mod,libata

I am able to connect my camera, thumbdrive, handset, joystick, gamepad and wireless adapter via USB, but not this.

The unit connects fine to my winXP system at work.  On that same machine, if I run Knoppix I have the same error.  I have also had the same problem on  my old Fedora box.  Since this works with windows, and since I have the same problem on other machines, I know that this isn't a hardware problem on my box.

It seems like the firmware on this unit works better with Windows than Linux.

Has anyone here had any luck dealing with this problem?

Thanks.[/FONT]

---

### Post by adzik on 2007-09-17
Just to follow up with this, I know it's a little late in coming, but I have spoken with support about functionality under linux, through email at two different support centers this company uses for this MP3 player.
Anyway, the long and short answer was, "no, it was only designed for M$ Windows". 
Since we are dealing with something that needs a usb driver on some level, anyone with this device is left out in the cold for now.
I was desperately looking for a solution myself a little while back and found no answers, and since I am not a programmer and don't know the first thing about it, I sure wasn't going to pull a device driver out of my butt any time soon.
If you want this thing to work, you'll need some patience...
Anyway, because I have been know to be creatively cheap sometimes, I did find a very unusual workaround with my Playstation 2 that does allow me to transfer files on my computer...   8-)   Obviously this only helps people with a PS2 (or PS3 possibly)
Also there is another unusual way that you may be able to access this device on feisty or whatever you are using.
The device needs to be fully recharged, then for some reason the system detects it as a usb "karaoke" device. Still not usable but detectable.
Fire up VirtualBox, load it with Windows whatever (98 & higher), and add the (fully recharged) "karaoke device" in the list of USB devices you want your VM to use.
But this method may or may not be 100% effective. 

Hope this helps anyone with this nasty little player.

---

