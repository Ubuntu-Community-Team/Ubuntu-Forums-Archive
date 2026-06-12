---
title: "How can I know who is using a module?"
date: 2007-10-11
forum: General Help
---

### Post by Hxsrmeng on 2007-10-11
I'd like to rmmod a module, but it shows the module is in use. 

How can I know who is using it?

Thanks.

---

### Post by Martin Witte on 2007-10-11
lsmod shows that

---

### Post by Hxsrmeng on 2007-10-11
Thanks. But it only showed the module is used by "1", the count.

---

### Post by bettlebrox on 2007-10-11
lsmod |grep modulename

For example, if I want to see what's using ndiswrapper:
[INDENT] lsmod |grep -i ndiswrapper
ndiswrapper           185240  0 
usbcore               138248  4 ndiswrapper,ehci_hcd,uhci_hcd[/INDENT]

Shows, ndiswrapper and the module that's using it (usbcore).

---

