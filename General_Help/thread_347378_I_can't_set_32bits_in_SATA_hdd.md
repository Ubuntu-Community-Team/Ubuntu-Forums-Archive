---
title: "I can't set 32bits in SATA hdd"
date: 2007-01-27
forum: General Help
---

### Post by braintheboss on 2007-01-27
sudo hdparm -c3 /dev/sda

/dev/sda:
 setting 32-bit IO_support flag to 3
 HDIO_SET_32BIT failed: Invalid argument
 IO_support   =  0 (default 16-bit)

I have a laptop HP nx9420.

Somebody can help me?

---

### Post by dcstar on 2007-01-27
> **braintheboss said:**
> sudo hdparm -c3 /dev/sda

/dev/sda:
 setting 32-bit IO_support flag to 3
 HDIO_SET_32BIT failed: Invalid argument
 IO_support   =  0 (default 16-bit)

I have a laptop HP nx9420.

Somebody can help me?
```
sudo hdparm -iI /dev/sda
```
will show you the current settings and capabilities of that drive, you will see if it is in fact capable of accepting your command.

---

