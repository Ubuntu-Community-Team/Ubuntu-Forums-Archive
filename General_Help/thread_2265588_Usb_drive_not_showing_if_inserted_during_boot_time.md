---
title: "Usb drive not showing if inserted during boot time but showing if inserted after log"
date: 2015-02-16
forum: General Help
---

### Post by srinath4 on 2015-02-16
I use an USB external hard-drive. The drive shows up fine on inserting the drive after logging in to my account but if I insert the drive during boot time, it doesn't show after logging in, even if I remove and re-insert. But the device lights up each time. Is this a bug or is there a way to fix this?

I am on Ubuntu 14.04 Desktop.
This is my first post, so please guide on posting-rules violations, if any.

---

### Post by Holger_Gehrke on 2015-02-16
The drive not showing up if it's connected before login is expected behaviour. Nothing gets mounted during boot that isn't in /etc/fstab. But the drive not getting mounted if removed and reinserted is strange. You could try leaving it disconnected for a longer time, so the system can be sure it's gone or inserting it into a different port.

---

