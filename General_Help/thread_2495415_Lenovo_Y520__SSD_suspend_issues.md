---
title: "Lenovo Y520  SSD suspend issues"
date: 2024-02-18
forum: General Help
---

### Post by djstrong on 2024-02-18
I have replaced my disk with 990 PRO PCle 4.0 NVMe M.2 SSD 4TB in Lenovo Y520 and I have big problems with suspend on Ubuntu 23.04.

---

### Post by oldfred on 2024-02-18
Moved to your own thread as different issue than original post.

Have you updated UEFI firmware & SSD firmware to latest available.
Compare these to vendors's support page for your system.
sudo lshw | grep -m 1 -A 5 "*-firmware"
udisksctl status

My Samsung SSD had an update and it was a bootable ISO with just  a newer firmware.
How to update Samsung:
[https://wiki.archlinux.org/index.php/Solid_state_drive](https://wiki.archlinux.org/index.php/Solid_state_drive) & 
[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)
Look at firmware, not Magician which is Windows.

---

