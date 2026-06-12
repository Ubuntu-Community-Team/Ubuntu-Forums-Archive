---
title: "Add Windows 7 to GRUB"
date: 2013-05-27
forum: General Help
---

### Post by davevez on 2013-05-27
Hi, 

I installed windows 7 to HDD. Then I installed Ubuntu to SSD. There is no option for Windows 7 boot in GRUB now.

Can you help me please?

---

### Post by prodigy_ on 2013-05-27
Open terminal and run ```
sudo update-grub
```

---

### Post by mastablasta on 2013-05-27
use  boot repair tool to repair bootloader
_[COLOR=#810081][https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)[/COLOR]_

or command line to update grub:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by martinr on 2013-05-27
Start the Live CD with a non UEFI boot sequence if you have an msdos/MBR (non GPT) structured HD with Win7 on it and install Ubuntu again.
See [this solution]("http://ubuntuforums.org/showthread.php?t=2003442").

---

