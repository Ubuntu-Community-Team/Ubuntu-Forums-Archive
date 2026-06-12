---
title: "Dual boot wubi/lupin"
date: 2007-06-17
forum: General Help
---

### Post by wd5gnr on 2007-06-17
I've used topologilinux in the past. I was wondering how hard it might be to do something similar with the Wubi setup. It seems like using virtualbox (open source) or Parallels (not open) that it might be workable. The problem is getting access to the loop file in the virtual machine AND at native boot time.

A few untested ideas:

1) Let the normal "bare" boot work as it does now. For virtual mode, let grub do a boot to a shared drive that contains the loop file. This would be a problem though since I don't think you have enough infrastructure to get to a SAMBA drive at boot time.

2) Install the loop file to a USB drive which the VM could also see. This assumes that both grub and Virtualbox or similar would support booting from the USB drive.

Any other ideas? Has any of this been tried?

---

