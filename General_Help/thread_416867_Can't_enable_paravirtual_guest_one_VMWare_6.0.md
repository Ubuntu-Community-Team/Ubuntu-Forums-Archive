---
title: "Can't enable paravirtual guest one VMWare 6.0"
date: 2007-04-21
forum: General Help
---

### Post by kimus on 2007-04-21
I have ubuntu 7.04 but I can't enable a paravirtual guest on VMWare 6.0. The VMI support is required for this to work.

How can I see if the kernel has VMI support?

---

### Post by kimus on 2007-04-22
I found out that I can enable the checkbox in a Linux guest not in a Windows guest. I posted this question on the [VMWare forum]("http://www.vmware.com/community/thread.jspa?threadID=81410&tstart=0").

---

### Post by darwin_te on 2007-06-27
The paravirtual kernel support is available only when running Linux guest.  If you're running Windows guest, it is disabled.  Also your Linux guest kernel should have support for VMI.

To enable VMI on the Linux guest, edit its VMX config file:

vmi.enabled = "TRUE"
vmi.pciSlotNumber = "-1"

---

