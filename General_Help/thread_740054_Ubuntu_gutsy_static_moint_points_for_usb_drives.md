---
title: "Ubuntu gutsy static moint points for usb drives"
date: 2008-03-30
forum: General Help
---

### Post by pmbsa on 2008-03-30
Hi, I am trying to get ubuntu to mount my usb drives to static points but I cant seem to get it right, I have tried pretty much everything I have seen documented on this and other forums but nothing seems to work.
I have tried changing hall, I have added udev rules... pretty much the lot, I would appreciate some help if anybody is any the wiser.

thanks

---

### Post by mcduck on 2008-03-30
Just add entry lines for your drives in /etc/fstab, using the UUID number for your drives so it doesn't make any difference if their device name changes.

You can get the UUIDs for your partitions with the 'blkid'-command.

---

### Post by pmbsa on 2008-03-30
thanks for the tip, I get an error "you are not privileged to mount this volume" though, any idea?

--- Never mind, I was being thick!... its all working fine now, thanks for the help!--

---

