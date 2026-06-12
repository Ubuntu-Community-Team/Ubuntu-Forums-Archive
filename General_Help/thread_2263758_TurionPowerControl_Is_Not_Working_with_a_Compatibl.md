---
title: "TurionPowerControl Is Not Working with a Compatible Processor"
date: 2015-02-03
forum: General Help
---

### Post by junior6 on 2015-02-03
I've installed TurionPowerControl to undervolt my AMD A6-3400M processor, but receive the following output:

> tpc -l
TurionPowerControl 0.44-rc2 (export)
Turion Power States Optimization and Control - by blackshard


cpuid:open: Permission denied
cpuid:open: Permission denied
cpuid:open: Permission denied
cpuid:open: Permission denied
cpuid:open: Permission denied
No supported processor detected, sorry.

[COLOR=#000000][FONT=arial]**"**TurionPowerControl, despite its name, allows to view and control many parameters of modern AMD processors. It can manipulate power states, frequencies, DRAM timings, power settings and can report temperatures, monitor pstate changes and precise cpu usage. It is available for Windows and Linux, for both 32 bit and 64 bit architectures and fully supports multiprocessor machines.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Currently supported processors are:[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]- Family 10h: All Phenom, Phenom II, Athlon II, Turion Mxxx and Pxxx processors[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]- Family 11h: Turion ZM/RM and Athlon QL processors[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]**- Family 12h: Llano A-series processors (partial and experimental support), beginning from version 0.41**[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]- Family 14h: Ontario C-series, Zacate E-series processors (partial and experimental support), beginning from version 0.41[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]- Family 15h: Bulldozer platform (FX Series, Interlagos and Valencia server platforms)**"**[/FONT][/COLOR]

---

### Post by Yellow Pasque on 2015-02-03
Read the troubleshooting section:
[https://code.google.com/p/turionpowercontrol/wiki/CompilationAndInstallation](https://code.google.com/p/turionpowercontrol/wiki/CompilationAndInstallation)
You need to run it as root/sudo and you need to load the appropriate modules.

---

### Post by junior6 on 2015-02-03
> **Temüjin said:**
> Read the troubleshooting section:
[https://code.google.com/p/turionpowercontrol/wiki/CompilationAndInstallation](https://code.google.com/p/turionpowercontrol/wiki/CompilationAndInstallation)
You need to run it as root/sudo and you need to load the appropriate modules.

I've figured it out, but thank you. There is another module (i2c-dev) that isn't listed on their site which had to be installed and loaded.

---

