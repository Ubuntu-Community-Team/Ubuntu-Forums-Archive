---
title: "Question regarding pci=nocrs."
date: 2014-07-20
forum: General Help
---

### Post by RJSmith92 on 2014-07-20
Hello All,

I have a question regarding how 'pci=nocrs' works.

When this is set, does the OS then enumerate the PCI devices itself ignoring what the ACPI BIOS set them as, if so how does it know the range of addresses that the PCI host bridge forwards on, does it just use the range from 'top of memory' to 4GB?

if this option is set to 'pci=use_crs', what does this make happen? The OS now knows the PCI host bridge window, so it can more confidently assign resources?

Any help with this would be greatly appreciated.

Thanks.

---

### Post by RJSmith92 on 2014-07-20
Hello All,

I have a question regarding how 'pci=nocrs' works.

When this is set, does the OS then enumerate the PCI devices itself ignoring what the ACPI BIOS set them as, if so how does it know the range of addresses that the PCI host bridge forwards on, does it just use the range from 'top of memory' to 4GB?

if this option is set to 'pci=use_crs', what does this make happen? The OS now knows the PCI host bridge window, so it can more confidently assign resources?

Any help with this would be greatly appreciated.

Thanks.

---

### Post by QIII on 2014-07-21
Threads merged.

---

### Post by RJSmith92 on 2014-07-21
Thanks QIII.

---

### Post by RJSmith92 on 2014-07-22
Anyone?

---

