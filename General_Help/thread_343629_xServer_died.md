---
title: "xServer died"
date: 2007-01-21
forum: General Help
---

### Post by llanitedave on 2007-01-21
I'm running 6.10 on a G4 Apple iBook.  I'm not sure if that part matters...

It's been running for months with no problems.

As of today, when I boot up, there's no Xserver -- it boots into tty mode only.

If I try to run an app such as Kate from the command line, the response is 
"cannot connect to x  server"

Should I reinstall Edgy?
I have a USB stick that I should be able to save all my really vital documents to, but I can't find the usb port:  it's not in /media or /mnt.

Of course, I'd rather simply figure out how to reactivate the x server.

Any ideas?

---

### Post by llanitedave on 2007-01-21
Update:  I tried 'startx' from the command line, and this is the response:

...
(==) Using config file: "etc/X11/xorg.conf"
(WW) RADEON: No matching device section for instance (BusID PCI:0:16:0) found
(EE) Screen 0 deleted because of no matching config section.
(**) RADEON(0): RADEONFreeScreen
(EE) Device(s) detected, but none match those in the config file.

This tells me my xorg.conf file is corrupted.

Looking at my xorg.conf file, I do see a line that reads:

busid "PCI:0:16:0"

It's there twice, in fact:  under the section "Device"

and under the section "device" #

Is there something I can change in the xorg.config file?

(BTW, I know it's not the hardware, because OS X still boots up fine)

---

### Post by llanitedave on 2007-01-21
The xorg.conf file provided its own instructions for a fix.

I ran the following command:

sudo dpkg-reconfigure -phigh xserver-xorg

That showed me where the mismatch was:  although the os correctly detected the ATI radeon graphics card, the driver that was assigned was not an ATI driver.  I'm at a loss to explain how THAT happened. The driver name was one I'd never heard of, possibly just a random combination of letters.

I manually reassigned the driver to ATI, rebooted, and everything cleared up.

I'm SO glad I didn't have to reinstall everything!

---

