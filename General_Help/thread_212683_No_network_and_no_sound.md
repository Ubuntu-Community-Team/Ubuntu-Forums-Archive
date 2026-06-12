---
title: "No network and no sound"
date: 2006-07-10
forum: General Help
---

### Post by garton on 2006-07-10
I just installed Ubuntu 6.06. My onboard NIC does not work and my onboard sound card does not work

My motherboard is a Asus K8U-X, which has a M5263 ethernet controller. The sound chip is a M5455 multimedia controller. (This info comes from lspci.)

mii-diag and/or mii-tools says that the device does not support the operation, or something along those lines.

If I insert a PCI network card into the computer, networking comes alive without a hitch, using eth1 instead.

Does anyone know what I can do to bring the M5263 and the M5455 controllers to life? Thanks!

---

