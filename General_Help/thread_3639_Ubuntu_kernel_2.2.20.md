---
title: "Ubuntu kernel 2.2.20 ???"
date: 2004-11-08
forum: General Help
---

### Post by stevho on 2004-11-08
:confused: 'uname -a' reports "Linux ... 2.2.20-idepci ... i686" ! ?

When I boot and shutdown I get multiple error messages like:
"Can't open dependencies file /lib/modules/2.2.20-idepci/modules.dep (No such file...)"

When I try to modprobe I get the same message.

The first line in dmesg begins "Linux version 2.2.20-idepci..."
and before this line in /var/log/messages I have:-
"Cannot find map file
No module symbols loaded"
The only directory I have in /lib/modules/ is '2.6.8.1-3-386' which is surely correct.

Where does uname get its info from?
and why doesn't the kernel look in the correct path for its modules?

Thanks

---

### Post by jdong on 2004-11-08
Ubuntu doesn't have a 2.2 kernel. If you installed Ubuntu, you should never ever have any other kernel than 2.6.8.1-3-xxx.

It might be a coincidence, but 2.2.20-idepci is the default kernel for **debian woody**.

---

