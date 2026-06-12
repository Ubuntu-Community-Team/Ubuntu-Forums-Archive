---
title: "how does one unmounts their usb mouse?"
date: 2007-05-29
forum: General Help
---

### Post by eentonig on 2007-05-29
I noticed some annoying behavior recently.

Everytime I unplug my usb mouse to use that port for another appliance, shortly after the system will hang and become unresponsive. (switching to another vty doesn't help. I can switch, but not login.)

I get an error message about an IO operation to an unavailable device. At first, I thought is was related to the USB HD I normally use at that moment. But now I found that it also happens with other usb HW.

So I figured this is because I yank out the USB and I can accept it. But I still do need that port from time to time. (I only have three USB ports. 1 used for the mouse, 1 used for the usb disk that contains my Ubuntu installation. 1 used in those occasions for another USB Backup disk.) So, I'm looking for a way to unmount the mouse on my laptop (and only use the touchpad for a little while).

(I've got a workaround by attaching one of my backup HD to another old laptop and ssh to that to access the drive. But this is not elegant and unnecessary slow.)

---

### Post by JSThePatriot on 2007-05-29
I certainly wouldn't have thought that to be a problem, but I suppose it is. Usually you wouldn't need to "unmount" a mouse due to it not having actual data transfer. I would recommend you purchase a small travel USB Hub. That should solve your issues, and won't set you back much.

JS

---

### Post by fragos on 2007-05-29
I haven't seen this problem with a mouse but my Wacom tablet needs to have the driver restarted when I plug the tablet into a running system.  Perhaps a similar action can restore your mouse but I'm not sure what driver that would be.  The little travel hub sounds like the best solution.

---

### Post by gridsleep on 2007-05-29
Don't waste money on a USB hub.  It won't work either.  The problem is that the whole USB subsystem cuts out and none of the USB hubs work again until after a reboot.  I'm having this problem on my Toshiba, and others are having similar problems.  There appears to be some USB driver issue possibly related to Realtek hardware.  So far no official response from the Ubuntu support in the forums, as far as I've found.  Keep reading the forums.

---

