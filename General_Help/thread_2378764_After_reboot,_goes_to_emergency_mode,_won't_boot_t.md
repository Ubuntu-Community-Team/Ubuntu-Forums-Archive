---
title: "After reboot, goes to emergency mode, won't boot to USB, goes straight to grub"
date: 2017-11-26
forum: General Help
---

### Post by johndoeiii on 2017-11-26
Hi yall,

Here is my issue, I am running an old HP laptop (F111DX) as a HTPC running Ubuntu Budgie.  It was running kind of buggy, so I did a quick reboot, after I rebooted it went to emergency mode and after rebooting again, grub would load, but then it would go back to emergency mode.  So I tried booting from the USB I used to install it and even with the USB set as the first to boot, it still goes to GRUB and then emergency mode.  Pressing Ctrl + D does nothing, it will eventually go back to the emergency mode screen.  Any help is appreciated.  Would like to get this fixed tonight if possible.  Thank you and have a  great night.

---

### Post by jaweewo on 2017-11-27
Can you write journalctl -xb and upload the output? Thanks.

---

