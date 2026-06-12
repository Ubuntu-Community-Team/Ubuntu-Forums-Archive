---
title: "[SOLVED] Stoopid Question from a Noob"
date: 2007-06-24
forum: General Help
---

### Post by L8erG8er on 2007-06-24
What is the best way to punch up version info, for the kernel, Ubuntu (even though I know what it is already) and Xorg?

Thanks!

---

### Post by Swab on 2007-06-24
Well for the kernel you can do: uname -r

Not sure about X.

---

### Post by AlexThomson_NZ on 2007-06-24
Kernel version:
uname -a

Xorg:
cat /var/log/Xorg.0.log | grep "X Window"

Ubuntu- not too sure.  Maybe something like:
dmesg | head -1

---

### Post by Ayuthia on 2007-06-24
Ubuntu version: cat /etc/issue

Xorg: Xorg -version

---

### Post by fdrake on 2007-06-24
Xorg -version (see man Xorg)

oh never mind somebody else posted already

---

### Post by L8erG8er on 2007-06-24
That helps a lot.  Thank you all.  That is exactly what I am looking for.

---

