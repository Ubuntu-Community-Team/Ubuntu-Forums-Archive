---
title: "Speeding up default OS countdown on boot"
date: 2008-05-09
forum: General Help
---

### Post by schauerlich on 2008-05-09
Currently, after BIOS, the menu allowing you to choose between XP and Ubuntu times out and defaults to XP after 15 seconds. I'd like to speed this up to 3 seconds or so. I tried editing /boot/grub/menu.lst 

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3
```However, this only speeds up the GRUB stage 2 timer once you've selected Ubuntu. What file do I edit to speed up the first menu's timer?

EDIT:
Nevermind, I think found it myself. For anyone else who finds this thread, I edited /host/boot.ini

---

