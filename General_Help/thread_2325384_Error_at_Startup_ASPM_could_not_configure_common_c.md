---
title: "Error at Startup: ASPM could not configure common clock"
date: 2016-05-21
forum: General Help
---

### Post by qay1n on 2016-05-21
Hello,

At start up I am greeted with an error: ```
[    1.160030] pci 0000:00:01.0: ASPM: Could not configure common clock
```

I am on an ASUS Republic of Gamers g75vx laptop 64 bit.

Ubuntu 16.04
Nvidia drivers 361.42
Linux Kernel Version 4.5.5

DMESG output:
```

null@null:~$ dmesg | grep ASPM
[    0.123876] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.150941] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.151302] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    1.160030] pci 0000:00:01.0: ASPM: Could not configure common clock


```

Unsure how to proceed to fix this issue, it hasn’t affected anything noticeable.

---

### Post by qay1n on 2016-05-22
bump

---

### Post by qay1n on 2016-05-28
...bump :(

---

### Post by mightyiam on 2017-01-28
If it is any help, here is the line in the kernel that prints this message, it seems:
[https://github.com/torvalds/linux/blob/e53f9a28bee35932a0ae4d2ec2784f55491ec6d3/drivers/pci/pcie/aspm.c#L242](https://github.com/torvalds/linux/blob/e53f9a28bee35932a0ae4d2ec2784f55491ec6d3/drivers/pci/pcie/aspm.c#L242)

I'm having this happen in my laptop, as well. Would like to know what it means. It has to do with:
[https://en.wikipedia.org/wiki/Active_State_Power_Management](https://en.wikipedia.org/wiki/Active_State_Power_Management)

---

### Post by mightyiam on 2017-01-28
[http://superuser.com/questions/1172743/aspm-could-not-configure-common-clock](http://superuser.com/questions/1172743/aspm-could-not-configure-common-clock)

---

