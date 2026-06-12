---
title: "Ubuntu wont suspend from usb hdd"
date: 2012-11-07
forum: General Help
---

### Post by Harry.k on 2012-11-07
I installed 12.10 on a USB hard disk. It booted fine, and ran smooth. The problem is that i cant suspend or hibernate it. It wont even suspend if the battery is low. It just keeps running till the battery dies. That brings me to the next issue, last night it ran out of charge when i was away, and the boot-up speed is now soooo slooow. from 30 seconds, the boot-up time jubootupmped to some 4 minuts or so. Any suggestions?

---

### Post by efflandt on 2012-11-08
The reason it may have rebooted slowly is because if it powered off without shutting down properly it considers the partitions unclean and runs fsck to check them when it boots.    Although, if it continues to boot slowly on subsequent boots, not sure what the issue is.

I have never had any luck doing suspend or hibernate when booted from USB.  So it is probably best to set power settings to shutdown when lid is closed, power button pressed, or low battery.

---

### Post by Harry.k on 2012-11-08
The slow boot is a completely different issue.
[http://ubuntuforums.org/showthread.php?p=12343231#post12343231](http://ubuntuforums.org/showthread.php?p=12343231#post12343231)

As for this, it suspends fine from a pendrive, but not an external hdd. Heck, even the pendrive refused to suspnd when the external hdd was plugged in. It just went to the tty login instead.

---

