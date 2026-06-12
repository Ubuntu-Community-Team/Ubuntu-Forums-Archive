---
title: "Create a lightweight Ubuntu for embedded applications"
date: 2007-11-17
forum: General Help
---

### Post by mojo on 2007-11-17
**Rationale:** Andy is responsible to develop the OS for the VIA EPIA PX10000G. The OS must be extremely lightweight and up-to-date with latest Linux kernel. The storage media includes USB Pendrive, Flash cards and CD. The shell is unnecessary for the final product because the softwares are self-interaction daemons. The system should be loaded from RAM to reduce the times writing on the Flash media. Furthermore, persistence USB mode should be enabled for daemon making changes to the filesystem.

**Implementation:** I would like to ask experts on the forum on how to strip off the Ubuntu to the maximum. How to safely determine which static library is needed and how to remove busybox out of initramfs.

**Reference:**
Eagle Linux at [http://lwn.net/Articles/181371]("http://lwn.net/Articles/181371")/

---

