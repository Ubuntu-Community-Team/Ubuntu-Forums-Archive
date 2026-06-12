---
title: "ubuntu 20.04 suspend not working"
date: 2020-08-04
forum: General Help
---

### Post by naib864 on 2020-08-04
I bought a new laptop and installed ubuntu on it; Everything works fine except for suspend. The XHC device (USB 3.0, i think?) keeps waking up the system whenever I suspend it.
When I change the entry for XHC to disabled in /proc/acpi/wakeup it will work after I saved it, but half a minute later it is set to enabled again.
How can I prevent the system to re-enable wakeup-permissions for that USB-port?
Alternatively: How can I prevent the USB-port from trying to wake up the system in the first place?

---

