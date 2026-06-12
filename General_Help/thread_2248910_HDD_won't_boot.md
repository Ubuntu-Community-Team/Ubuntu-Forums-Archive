---
title: "HDD won't boot"
date: 2014-10-18
forum: General Help
---

### Post by guber90 on 2014-10-18
Hi guys I removed win7 from my pc and I decided to remove 100 mb partition that win makes. After that my hdd won't boot linux anymore. Any way to fix this?

---

### Post by TheFu on 2014-10-18
Try **boot-repair** - links in my signature.

On a dualboot system here, the Windows updates a few days ago left it with a GRUB REPAIR> prompt after reboot. Boot-repair fixed it. I expected to have to manually run grub-install, but didn't. I have no idea what it did, just that it works now. ;)

---

### Post by yancek on 2014-10-18
Which bootloader were you using?  If you were booting both with Grub it shouldn't have mattered.  The 100MB windows partition was probably its boot partition.

---

### Post by pe1992ter on 2014-10-18
if you don't have grup you could run a live cd and install or update grub sometimes grub fails

---

