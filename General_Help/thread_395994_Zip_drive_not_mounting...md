---
title: "Zip drive not mounting.."
date: 2007-03-28
forum: General Help
---

### Post by billdotson on 2007-03-28
my zip drive is not mounting.  My python programs are on it so I cannot get to them.  I have the options of mounting removable media automatically on and my flash drive works but not the ZIP. 

Well actually now the USB flash drive isn't mounting either.  Odd

my ZIP drive doesn't even seem to be getting any power.  The light on the flash drive is on but it isn't mounting.  I am running Ubuntu right now off of my external USB2.0 HDD and bothmy mouse and keyboard are USB so there are obviously 3 ports that are working.  I went upstairs and plugged the xip drive into the PC running Windows and it got power pretty fast.  What is going on?

---

### Post by acormack on 2007-03-30
have you tried running the mount command manually to mount the devices.

Does that work?

---

### Post by billdotson on 2007-03-30
I did sudo mount -a and nothing

---

### Post by acormack on 2007-03-30
what would be useful would be to see what happens in the /var/log/debug log when you plug in the USB zip.


open up a terminal and type 

sudo tail -f /var/log/daemon

Then plug in the device there should be lines output as the USB device is detected.  Here are the ones that I get when I plug in my USB memory stick

Mar 30 18:11:29 localhost kernel: [17216981.012000] usb-storage: device found at 4
Mar 30 18:11:29 localhost kernel: [17216981.012000] usb-storage: waiting for device to settle before scanning
Mar 30 18:11:34 localhost kernel: [17216986.012000] **sda**: Mode Sense: 03 00 00 00
Mar 30 18:11:34 localhost kernel: [17216986.016000] sda: Mode Sense: 03 00 00 00
Mar 30 18:11:34 localhost kernel: [17216986.016000] usb-storage: device scan complete

In the example above my system detected the device as **/dev/sda**

then try mounting it under /tmp using the following commands

mkdir /tmp/zipdrive
sudo mount /dev/sda /tmp/zipdrive

if you get no errors type

sudo find /tmp/zipdrive


and see what happens.  Please post the results.


Alec

---

