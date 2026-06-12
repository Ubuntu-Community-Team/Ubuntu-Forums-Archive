---
title: "USB to serial device"
date: 2007-03-29
forum: General Help
---

### Post by jjakspaw6 on 2007-03-29
Hi All, 
I'm still kinda new to Linux and I am having some trouble with a usb device, :) 
I am working with an Impro RH usb communications device. this device is part of an Impro Access control system. The RH also use the CP2101 driver.
I am trying to get this device to link to ttyS0. The RH is installed and shows up properly. Can some one give me an idea as to how to link these devices? 
The RH, has a listing in the dev/bus/usb/001/ directory.If I look in the device manager app I see that it is listed there as an IMPROX USB device (which is proper). A funny thing that happens though, when I disconnect and reconnect the equipment to the PC right now the device is listed as 003, if I disconnect and reconnect it, it will become 004. Is there a way that I can set the usb address permanently? 


Thanks

Jason

---

### Post by koma77 on 2007-03-29
Hmm. What do you mean by:
"I'm trying to get this device to link to ttyS0"?

If the device presents itself as a serial port it would probably show up as ttyUSB0 or so. (Or at least my USB devices that imitate a serial port does so)

Or are you trying to get your USB device to talk to another unit that is connected to your computers serial port?

---

### Post by jjakspaw6 on 2007-03-29
The Device doesn't show up as a ttyUSB* at all. Maybe there is a second driver that has to be loaded here (in windows we load the 2 drivers ....)

---

### Post by skypa on 2007-06-19
Hey man,

I don't know if this still matters, but I stumbled across the same problem this week. 
The Improx devices need the **cp2101** module to be loaded. Since the Improx devices aren't recognized by the module by default, you need to add the Improx device's **vendor and product ID** to the **kernel module source** and rebuild the module. 
After copying the newly built module to it's designated location and loading it, a new device (most likely /dev/ttyUSB0) will show up. You need to **delete i.e. /dev/ttyS2 and create a symbolic link to /dev/ttyUSB0**. After that, your ImproNet tools will be able to access the device through "COM3" as if using Windows.

If you need to, I'll be happy to elaborate all necessary steps. :)

---

