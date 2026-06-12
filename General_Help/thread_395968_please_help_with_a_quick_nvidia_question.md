---
title: "please help with a quick nvidia question"
date: 2007-03-28
forum: General Help
---

### Post by jputman01 on 2007-03-28
im using an hp notebook amd64 with supposedly nvidia go6150, i installed the nvidia driver from "add/remove" and enabled the drive with the instructions in "add/remove" and this is the error i got when i rebooted.

(WW) nvidia: no matching Device section for instance (BusID PCI:0:10:3) found


can anyone tell me what this means? i have no nvidia card?


thanks for the help and im using feisty

---

### Post by dcstar on 2007-03-29
> **jputman01 said:**
> im using an hp notebook amd64 with supposedly nvidia go6150, i installed the nvidia driver from "add/remove" and enabled the drive with the instructions in "add/remove" and this is the error i got when i rebooted.

(WW) nvidia: no matching Device section for instance (BusID PCI:0:10:3) found


can anyone tell me what this means? i have no nvidia card?


thanks for the help and im using feisty

In a terminal:

```
sudo dpkg-reconfigure xserver-xorg
```
and go through the steps.

If that doesn't work do a search for the numerous nvidia troubleshooting posts in this forum.

---

