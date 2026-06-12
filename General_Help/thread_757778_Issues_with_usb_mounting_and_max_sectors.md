---
title: "Issues with usb mounting and max_sectors"
date: 2008-04-17
forum: General Help
---

### Post by miatawnt2b on 2008-04-17
I've been having major issues with USB media reads/writes.  I've tracked the problem down to the fact that the USB controller is trying to send too much data to the device causing timeouts and disconnects.

I can solve the problem by typing the following two commands after a USB device is mounted.

sudo sh -c "echo 120 > /sys/block/sdc/queue/max_sectors_kb"
sudo sh -c "echo 120 > /sys/block/sdc/device/max_sectors"

It's kind of a pain to type this in all the time.  Is there a way to do the same thing automatically when the USB device mounts?

Thanks,
-J

---

### Post by mssever on 2008-04-18
I believe that you can create a udev rule for this. Google it, because I don't remember enough about udev to give specific instructions.

---

