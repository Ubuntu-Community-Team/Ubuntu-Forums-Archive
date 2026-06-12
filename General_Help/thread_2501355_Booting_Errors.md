---
title: "Booting Errors"
date: 2024-10-03
forum: General Help
---

### Post by mikodo on 2024-10-03
Xubuntu 24.04.x

sudo lshw 

```
description: Notebook
    product: HP Laptop 17-by2xxx (7PV35UA#ABL)
    vendor: HP
    version: Type1ProductConfigId
    serial: 5CG01388GL
    width: 64 bits

URL search for (7PV35UA#ABL)
```

When booting the laptop,  it stalls. 

journalctl -xb 

```
:~$ journalctl -xb
Oct 03 09:34:21 Mike-Laptop kernel: Linux version 6.8.0-45-generic (buildd@lcy0>
Oct 03 09:34:21 Mike-Laptop kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-6.8.>
Oct 03 09:34:21 Mike-Laptop kernel: KERNEL supported cpus:
Oct 03 09:34:21 Mike-Laptop kernel:   Intel GenuineIntel
Oct 03 09:34:21 Mike-Laptop kernel:   AMD AuthenticAMD
Oct 03 09:34:21 Mike-Laptop kernel:   Hygon HygonGenuine
Oct 03 09:34:21 Mike-Laptop kernel:   Centaur CentaurHauls
Oct 03 09:34:21 Mike-Laptop kernel:   zhaoxin   Shanghai

Oct 03 09:34:21 Mike-Laptop kernel: x86/cpu: SGX disabled by BIOS.

MMIO Stale Data CPU bug present and SMT on,>

ACPI BIOS Error (bug): Could not resolve sy>
Oct 03 09:34:21 Mike-Laptop kernel: 
Oct 03 09:34:21 Mike-Laptop kernel: No Local Variables are initialized for Meth>
Oct 03 09:34:21 Mike-Laptop kernel: 
Oct 03 09:34:21 Mike-Laptop kernel: No Arguments are initialized for method [_O>
Oct 03 09:34:21 Mike-Laptop kernel: 
Oct 03 09:34:21 Mike-Laptop kernel: ACPI Error: Aborting method \_SB.PCI0.RP05.>

ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.DGPV], AE_NOT_FOUND (20230628/psargs-330)
Oct 03 09:34:21 Mike-Laptop kernel: 
Oct 03 09:34:21 Mike-Laptop kernel: No Local Variables are initialized for Method [_ON_]
Oct 03 09:34:21 Mike-Laptop kernel: 
Oct 03 09:34:21 Mike-Laptop kernel: No Arguments are initialized for method [_ON_]
Oct 03 09:34:21 Mike-Laptop kernel: 
Oct 03 09:34:21 Mike-Laptop kernel: ACPI Error: Aborting method \_SB.PCI0.RP05.PCRP._ON due to previous error (AE_NOT_FOUND) (20230628/

```

Eventually following the prompts, I get the laptop to boot. (I am writing this report from the same laptop).

I have the whole report if you want it but, above are all the errors I saw.

I'm saving 'The UbuntuForums/System-info' script info, and  can send it too, if needed.

This behavior has been happening for the last week, I believe. 

What can I do?

Thanks

---

### Post by 1fallen on 2024-10-03
When's the last time you updated your Bios, and Firmware?

[https://askubuntu.com/questions/1333069/acpi-error-on-every-boot](https://askubuntu.com/questions/1333069/acpi-error-on-every-boot)
This link will give you some ideas.
Mine:
```
journalctl -xb|grep 'ACPI BIOS' 
Oct 03 13:43:22 cachyos-butter kernel: ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.PB2], AE_NOT_FOUND (20240322/dswload2-163)

```

I boot many Linux OS's from this machine, all report the same.
```
BIOS Information
        Vendor: LENOVO
        Version: HHCN36WW
        Release Date: 12/07/2023

```

---

### Post by mikodo on 2024-10-03
> **1fallen2 said:**
> When the last time you updated your Bios, and Firmware?

[https://askubuntu.com/questions/1333069/acpi-error-on-every-boot](https://askubuntu.com/questions/1333069/acpi-error-on-every-boot)

Thank you for the response and the link. To answer your question, I am embarrassed to say, Never. I'll look into doing that, to see if that helps.

---

### Post by andikleini on 2024-10-05
I have the sam issue with ubuntu on Tuxedo Notebook with Ubunto 22 and I could circumvent it by stepping back to kernel 6.8.0-40 (grub config modified …). The problem arised with kernel 6.8.0-45 which matches to the time when the problem was recognized above. My bios version is one minor step behind and I asked Tuxedo support for advice (I think they will suggest updating the bios).I will let you know here when I find something out.

---

