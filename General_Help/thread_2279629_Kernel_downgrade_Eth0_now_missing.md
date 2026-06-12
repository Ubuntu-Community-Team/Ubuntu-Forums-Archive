---
title: "Kernel downgrade Eth0 now missing"
date: 2015-05-25
forum: General Help
---

### Post by chris86wm on 2015-05-25
Due to compatibility issues with a piece of software I use, I needed to downgrade the kernel. I installed and booted into an older kernel (3.13.0-360), but now my ethernet adapter (eth0) is missing. I checked *ifconfig*, and it's no longer listed there. When I boot into the current kernel (3.13.0-53), the ethernet adapter is detected and functions like normal.

Any guidance on what I need to do to correct this?

Running Ubuntu Server - Trusty

---

### Post by nerdtron on 2015-05-25
Boot in the old kernel and see if the eth0 is still detected.
```
 dmesg | grep -i eth 
ifconfig -a
```

It probably have a different interface name or so (hopefully).

---

### Post by 45D2ev2uHl on 2015-05-25
Open up a terminal and check if your network is detected with *lspci*
If so try to bring it up with:

```
ifconfig eth0 up
```

---

### Post by dundel2 on 2015-05-25
Try to modprobe your network driver.

---

### Post by chris86wm on 2015-05-25
> **nerdtron said:**
> Boot in the old kernel and see if the eth0 is still detected.
```
 dmesg | grep -i eth 
ifconfig -a
```

It probably have a different interface name or so (hopefully).

ifconfig -a 
This only returned "lo". "Eth0" is not listed.

desmg | grep -i eth
returned 4 different ACPI errors. Nothing related to the network card.

---

### Post by chris86wm on 2015-05-25
> **45D2ev2uHl said:**
> Open up a terminal and check if your network is detected with *lspci*
If so try to bring it up with:

```
ifconfig eth0 up
```

My ethernet controller is listed when I run *lspci*, but *ifconfig eth0 up* returns "ERROR: No such device"

---

