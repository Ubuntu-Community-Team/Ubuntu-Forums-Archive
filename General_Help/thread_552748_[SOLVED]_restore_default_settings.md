---
title: "[SOLVED] restore default settings"
date: 2007-09-16
forum: General Help
---

### Post by g2g591 on 2007-09-16
[LEFT]Is there anyway to restore the default settings for a program/service? more specificly, I want to restore the default networking settings (use dhcp) because while i was trying to setup networking in a chroot for a gentoo install, apparently some of the commands excaped the chroot jail and screwed up my settings
[/LEFT]

---

### Post by AndyCooll on 2007-09-16
Easiest way to do that is either to change back to dhcp (System > Administration > Network) or manually edit the /etc/network/interfaces file, by hashing out the current settings then adding something along the lines of:
```
# The primary network interface
auto eth0
iface eth0 inet dhcp
```

:cool:

---

### Post by g2g591 on 2007-09-16
thanks

---

