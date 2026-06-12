---
title: "udev: Creating symlink for USB-Disk does not work during boot"
date: 2014-09-11
forum: General Help
---

### Post by AllesMeins on 2014-09-11
I want to create a special symlink for my external harddrive. For that I've created a udev-rule that works flawlessly, if I connect the drive while the system is already running. But nothing happens, if the drive is already connected during start-up. Is there anything special I've to consider if I want my rule to work on already connected devices?

```
KERNEL=="sd?", SUBSYSTEMS=="block", ENV{ID_SERIAL_SHORT}=="NA4KFWD0", SYMLINK+="extern_a2"
```

(saved to /etc/udev/rules.d/90-zuordnung.rules)

I'm using Ubuntu 14.04.

---

