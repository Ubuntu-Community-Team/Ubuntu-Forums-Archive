---
title: "PCI error messages on Lenovo B50-10"
date: 2016-12-17
forum: General Help
---

### Post by ragb1 on 2016-12-17
Hello:

- Recently I've installed Ubuntu LTS 16.04 on a new Lenovo B50-10 laptop. Apparently everything is working properly, however some error messages appears regarding pci devices on dmesg.

dmesg |grep fail
[    1.268776] pci 0000:00:1c.0: BAR 14: failed to assign [mem size 0x00200000]
[    1.268789] pci 0000:00:1c.0: BAR 15: failed to assign [mem size 0x00200000 64bit pref]
[    1.268803] pci 0000:00:1c.1: BAR 15: failed to assign [mem size 0x00200000 64bit pref]
[    1.268830] pci 0000:00:1c.1: BAR 15: failed to assign [mem size 0x00200000 64bit pref]
[    1.268839] pci 0000:00:1c.0: BAR 14: failed to assign [mem size 0x00200000]
[    1.268852] pci 0000:00:1c.0: BAR 15: failed to assign [mem size 0x00200000 64bit pref]

And some other messages like this:

[    0.537659] pci 0000:00:1c.1: BAR 15: no space for [mem size 0x00200000 64bit pref]

- I've searched this errors on google, and everything indicates it could be a bios bug.  Beside, a related error message appears on dmesg output, as you can see above:

[    2.867219] pci 0000:00:1d.0: EHCI: BIOS handoff failed (BIOS bug?) 01010001

- I've update the bios with the new version available on Lenovo support site, v2.07 at this point, released on Oct-2016, but the problem remains.

- If I pass the option 'acpi=off' to the kernel, no error messages appears, but wifi card doesn't work. 

- If a fix 'OS Optimized default' to Enabled on Bios, and hit 'Load default settings', the errors remain.

IMHO, everything is related with a bios bug. In the past, I've suffered a similar problem with a Lenovo b50-30, but in that case, a bios update fixed the problem.

Any help would be appreciate.

Thanks in advance,

Best Regards.

---

