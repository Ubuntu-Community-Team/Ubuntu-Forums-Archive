---
title: "[SOLVED] Dmesg Problems"
date: 2008-04-17
forum: General Help
---

### Post by Robbyx on 2008-04-17
When I start the machine I am getting an error message about the bios, after the flash screen,   but I can not read it in time and the pause does not work at that point.

I have therefore gone through the Dmesg listing to see if there are any problems listed there. These are what I can find. Should I be concerned about them, and what should I do to correct them. 

I have looked in the boot log and it shows as empty.

I am trying to get my new cpu e8200 to work on the current MB, but it is not posting on start up. The older pentium Smithfield is working in the same board.



```
[   54.472763] PnPBIOS: Scanning system for PnP BIOS support...
[   54.472772] PnPBIOS: Found PnP BIOS installation structure at 0xc00f5f00
[   54.472776] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x6f8a, dseg 0xf0000
[   54.473609] PNPBIOS fault.. attempting recovery.
[   54.473661] PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
[   54.473713] PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
[   54.473766] PnPBIOS: Check with your vendor for an updated BIOS
[   54.473816] PnPBIOS: get_dev_node: unexpected status 0x37

```

```
  54.522561] pnp: 00:00: iomem range 0x0-0x9a7ff could not be reserved
[   54.522564] pnp: 00:00: iomem range 0x9a800-0x9ffff could not be reserved
[   54.522568] pnp: 00:00: iomem range 0xe0000-0xfffff could not be reserved
[   54.522571] pnp: 00:00: iomem range 0x100000-0x7ffbffff could not be reserved
[   54.522584] pnp: 00:0a: ioport range 0xa00-0xadf has been reserved
[   54.522591] pnp: 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[   54.522594] pnp: 00:0c: ioport range 0xcf8-0xcff could not be reserved
[   54.522597] pnp: 00:0c: ioport range 0x4400-0x447f has been reserved
[   54.522600] pnp: 00:0c: ioport range 0x4480-0x44ff has been reserved
[   54.522603] pnp: 00:0c: ioport range 0x4000-0x407f has been reserved
[   54.522606] pnp: 00:0c: ioport range 0x4080-0x40ff has been reserved
[   54.522609] pnp: 00:0c: ioport range 0x4800-0x487f has been reserved
[   54.522613] pnp: 00:0c: iomem range 0xfed00000-0xfed00fff has been reserved
[   54.522616] pnp: 00:0c: iomem range 0x0-0x0 could not be reserved
[   54.522619] pnp: 00:0c: iomem range 0x0-0x0 could not be reserved
[   54.522621] pnp: 00:0c: iomem range 0x0-0x0 could not be reserved
[   54.522628] pnp: 00:0d: iomem range 0xe0000000-0xefffffff has been reserved

```

I do not know where to put the "pnpbios=off" option

```
[   55.620920] EISA: Probing bus 0 at eisa.0
[   55.620942] Cannot allocate resource for EISA slot 4
[   55.620945] Cannot allocate resource for EISA slot 5
[   55.620948] Cannot allocate resource for EISA slot 6

```



```
[   56.856757] AppArmor: AppArmor initialized<5>audit(1208469471.971:2):  type=1505 info="AppArmor initialized" pid=1168
[   56.866218] fuse init (API version 7.8)
[   56.872975] Failure registering capabilities with primary security module.
[   56.951411] thermal: Unknown symbol acpi_processor_set_thermal_limit

```

```
[  105.366604] ReiserFS: sdb6: checking transaction log (sdb6)
[  105.417870] ReiserFS: sdb6: Using r5 hash to sort names
[  107.564164] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[  107.564215] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[  107.564349] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[  107.564414] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[  108.198375] Failure registering capabilities with primary security module.

```

Robin

---

### Post by Robbyx on 2008-04-18
I am getting somewhere by following the advice at

[http://ubuntuforums.org/archive/index.php/t-37351.html](http://ubuntuforums.org/archive/index.php/t-37351.html)

---

