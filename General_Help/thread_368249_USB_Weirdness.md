---
title: "USB Weirdness"
date: 2007-02-23
forum: General Help
---

### Post by wej1971 on 2007-02-23
I've got a weird problem. I have a usb wireless dongle which sometimes works, sometimes doesn't, but when it stops working in Linux, if I turn my computer off and boot into Windows it doesn't work in Windows either. What's more, my usb mouse stops working as well, and I have to remove all usb devices except the mouse from the usb ports, reboot (sometimes more than once) until the mouse starts working and then plugin the other devices one by one.

Any idea why usb devices could be affected after a reboot?

---

### Post by nickoli_02 on 2007-02-23
hum... this sounds like a flaky hardware issue. Does it matter what usb slot you plug the dongle into to get it to stop working, or can you reproduce the failure in all slots? This may be time consuming. Also, you can try removing usb devices and see if you can still get it to fail (ie plug only the dongle and mouse into usb... dongle only... etc). 

It would also be useful to post the output of lsusb before and after your usb devices stop working.

---

### Post by wej1971 on 2007-02-23
It's always worked in Windows XP and I've never had this issue *until* I started using it in Linux and dual booting. What confuses me is how it can stop working in Linux, then continue to not work in Windows after several reboots. Eventually, after removing all USB devices and then adding one at a time it starts working again.

I will post lsusb output when I get back into Linux again.

---

