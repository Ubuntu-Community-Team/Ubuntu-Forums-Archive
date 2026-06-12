---
title: "External devices in readonly mode"
date: 2008-03-27
forum: General Help
---

### Post by abc7887 on 2008-03-27
all my external devices ie external hdd or pendrive are in read only mode in ubuntu....i cnt format thm,,paste or cut anything in them.....i cant even change the permissions as it says i am not the root..i tried browsing with nautilus but dint help...

---

### Post by abc7887 on 2008-03-27
plzz sum 1 rply...

---

### Post by -grubby on 2008-03-27
Well, here's a quick fix. In a terminal, type:

```
gksudo nautilus
```

This will enable Nautilus with root permissions, so you can make any changes desired to your devices. But, there is still more to solve..

---

### Post by ibuclaw on 2008-03-28
Plug in the device.

Open up a terminal.

Type in as normal user:
```
 pmount 
```
Then copy and paste the output in your next post.

Regards
Iain.

---

