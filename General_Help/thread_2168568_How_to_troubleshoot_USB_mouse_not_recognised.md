---
title: "How to troubleshoot: USB mouse not recognised?"
date: 2013-08-18
forum: General Help
---

### Post by mastablasta on 2013-08-18
It's a generic mouse (no brand, some chinese thingy). two buttons and a wheel. nothing special. it works in debian 6 (chriunchbang), winXP, win7 but not in kubuntu 13.04 doesn't recognise it. when i plug it in the mouse lits up but there is nothing under lsusb. it's like the USB port is empty. hwo do i trouble shoot? how do i make it recognised?

---

### Post by Erik1984 on 2013-08-18
That's weird indeed. Does anything pop up in the logs like the kernel log when you insert the mouse?

```
/var/log/kernel.log
```

---

### Post by mastablasta on 2013-08-19
so i tried to see what the log says. i plugin the mouse and no suddenly it works. strange. checked the log and lsusb an dit is recognised as creative labs optical mouse. oh well. solved i guess.

---

