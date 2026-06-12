---
title: "Boot failure"
date: 2013-08-18
forum: General Help
---

### Post by jason13 on 2013-08-18
After plugging in different hardware (and then reverting to the exact same configuration I had before) my computer hung up in a "boot failure" screen. It boots when I select "boot menu" in the bios screen and boot to my first HD. I checked my bios settings and they're exactly the same as they were. "HDD->optical drive->removable media->ethernet" and my HDD order is the order it should be. I noticed in the boot menu the ethernet option (IBA GE slot ***) appears first. Is there a way I can revert it so I don't have to intervene in the boot sequence?

---

### Post by decrepit on 2013-08-18
Not sure about this, but is it possible grub renamed the boot partition when you went with different hardware?
If so try doing grub update, that may fix it.

---

### Post by oldfred on 2013-08-18
I do not understand. You say hard drive is first, then say Ethernet is first. 
But those are BIOS settings and vary by vendor on how to change. Either screen should give a clue or you have to download manual and find instructions on how to change boot order. There may be two orders. One for device like HDD, USB, etc and then within HDD which hard drive. Which drive may be a sub-menu on device settings or even on a different page in BIOS configuration.

---

