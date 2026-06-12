---
title: "Dual boot Windows 7 not booting after upgrading from 14.04LTS to 16.04LTS"
date: 2019-03-09
forum: General Help
---

### Post by KieranFitzgerald on 2019-03-09
[COLOR=#000000]After upgrading to 16.04 Windows 7 not longer boots.
I ran boot repair from a live USB to no avail.

Report at [/COLOR][http://paste.ubuntu.com/p/zYPk8xDctp/](http://paste.ubuntu.com/p/zYPk8xDctp/)

Any ideas as to how to proceed

---

### Post by oldfred on 2019-03-09
You are showing UEFI Secure Boot on, Windows 7 does not support Secure Boot.

Grub only boots working Windows. Can you boot Windows directly from UEFI?

---

### Post by KieranFitzgerald on 2019-03-09
Changed secure boot in BIOS to "other OS".  All working thanks.
Set to solved

---

