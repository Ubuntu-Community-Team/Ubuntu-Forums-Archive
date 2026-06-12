---
title: "Unmount not working"
date: 2008-01-30
forum: General Help
---

### Post by Nonno Bassotto on 2008-01-30
I have a Nokia 6120c, and I mostly connect it via USB (data transfer mode). The problem is, each time I disconnect it, I receive the usual unmounting messages form Ubuntu, and wait until it says the device is ready for disconnection. I unplug it, and the phone alerts me that I have done an unsafe disconnection.

If I switch the computer off, instead, the device is correctly unplugged. What could be the problem? How do I really unmount it?

---

### Post by imtheguru on 2008-01-31
System > Preferences > Removable Drives and Media Preferences

Uncheck "Browse removable media when inserted"
also uncheck "Portable Music Players > Play music files when connected".

This will prevent the device from being remounted after umount.

Cheers.

---

### Post by peitschie on 2008-01-31
The actual unmount warning is generally displayed because the PC is trying to write data from its cache to the actual drive.  Linux caches the data writes, and trys to perform a single write to the external usb device (such as your phone).  Does your computer display this message every time or only on specific occasions?  Are you running any sync programs in the background?

---

### Post by Nonno Bassotto on 2008-02-01
> **imtheguru said:**
> System > Preferences > Removable Drives and Media Preferences

Uncheck "Browse removable media when inserted"
also uncheck "Portable Music Players > Play music files when connected".

This will prevent the device from being remounted after umount.

Cheers.

The device is not remounted: indeed the icon disappears from the desktop and mount -l doesn't show the device. Other removable drives unmount fine.

---

### Post by Nonno Bassotto on 2008-02-01
> **peitschie said:**
> The actual unmount warning is generally displayed because the PC is trying to write data from its cache to the actual drive.  Linux caches the data writes, and trys to perform a single write to the external usb device (such as your phone).  Does your computer display this message every time or only on specific occasions?  Are you running any sync programs in the background?

The message ("now you can remove...") is displayed only on certain occasions (I believe that this happens exactly when it has still to write some data). I don't sync anything, just use the device as a disk. Moreover this happens on two different computers, while both Mac and Windows unmount the drive just fine.

---

### Post by Nonno Bassotto on 2008-02-05
bump

---

### Post by celticbhoy on 2008-02-05
Your question is nothing to do with the way Ubuntu handles this operation, but the way the phone does it. I have an N80 and it works the same way. As long as you unmount in Ubuntu, and wait for a message that the drive has been unmounted you will be fine. The problem is that there is no way to come out of data transfer mode on the handset with it knowing all operations have finished.

---

### Post by Nonno Bassotto on 2008-02-06
Uhm... this makes sense. Still I wonder what happens when I shutdown the laptop, since before it is completely off, the message "you can now remove..." appears on the phone.

---

### Post by celticbhoy on 2008-02-07
I would guess that it is to do with the power being but to the usb port. The phone must detect that the usb is on longer operational.

---

