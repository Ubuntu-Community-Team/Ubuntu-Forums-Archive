---
title: "Wine and the 2.6.24-16 kernel"
date: 2008-04-22
forum: General Help
---

### Post by C. Wizard on 2008-04-22
Intalled 8.04RC and afterwards discovered that an old 16 bit windows program I've been running for years in WINE will no longer run.

Booted 8.04 with the older 2.6.22.14 kernel and it worked just fine.

Went back to the 2.6.24-16 kernel and tried to launch the program from a console and got the following error message:

preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:spoolsv:serv_main (0 (nil))
err:dosmem:load_winedos Could not load winedos.dll, DOS subsystem unavailable
winevdm: unable to exec '--app-name': 16-bit support missing

Anyone know a fix for this? Any help would be greatly appreciated.
Thank you very much.

---

### Post by C. Wizard on 2008-04-23
Just upgraded to WINE 9.60, and now it gives the following error message,

preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
fixme:spoolsv:serv_main (0 (nil))
winevdm: unable to exec 'H:\ahed\ahd3.exe': DOS memory range unavailable

WINE will run other ms products, such as office, which I really don't need as I prefer OpenOffice, but I use the old 16 bit "American Heritage Electronic Dictionary" program several times a day and would really like to get it working again.  
Any help would be greatly appreciated.
Thank you!
:)

---

### Post by PmDematagoda on 2008-04-23
Did you try asking this in the Wine forums? You may have better success there.

---

