---
title: "Udev won't start: hotplug"
date: 2014-08-16
forum: General Help
---

### Post by edo3 on 2014-08-16
Hi everybody,
during an upgrade of my VPS Ubuntu 14 server, udev won't start anymore. The init script says:

Configurazione di udev (204-5ubuntu20.4)...
 * udev requires hotplug support, not started
   ...fail!
invoke-rc.d: initscript udev, action "restart" failed.

Exploring /etc/init.d/udev, it seems that /sys/kernel/uevent_helper is missing.

Can you suggest me what could I do to solve it?

Thanks a lot!
Regards

---

