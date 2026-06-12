---
title: "No debuginfo of 4.15.0-133 kernel version"
date: 2021-03-31
forum: General Help
---

### Post by zacw2 on 2021-03-31
[COLOR=#242729][FONT=Arial]We have encountered a crash scenerio, core dump was generated within /var/crash without problem From dmesg.202103260914 it seems a memory access error during timer handle process, but we need to debug dump.202103260914 for root cause[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]But we could not found the debuginfo(linux-image-4.15.0-132-generic-dbgsym package) under Ubuntu official repository [http://ddebs.ubuntu.com/pool/main/l/linux/](http://ddebs.ubuntu.com/pool/main/l/linux/), it only have debuginfo of 4.15.0-130\4.15.0-132\4.15.0-134\4.15.0-135\4.15.0-136\4.15.0-137\4.15.0-139 kernel version[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Does any story here about why we lack of this kernel version debuginfo?[/FONT][/COLOR]

---

