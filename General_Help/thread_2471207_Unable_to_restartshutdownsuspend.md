---
title: "Unable to restart/shutdown/suspend"
date: 2022-01-23
forum: General Help
---

### Post by username0072 on 2022-01-23
I have been using Ubuntu 20.04.3 LTS for sometime without any issues on a AMD Ryzen 4700U mini pc. I could shutdown, restart, suspend without any issues but recently I am unable to do any of that. The system runs fine, but I am just unable to restart,shutdown or suspend anymore. When i try to restart I get stuck with 2 messages (see image), and nothing happens anymore no matter how long I wait

[IMG]https://i.imgur.com/8yec2Rz.jpg[/IMG]

Using the reboot command from terminal does nothing either (sudo reboot -f). It just shows Rebooting. but nothing happens and I can use the system normally

[IMG]https://i.imgur.com/HYg7P0z.jpg[/IMG]


I have updated my bios to the lates version, and I have tried reinstalling ubuntu multiple times, but it doesn't get fixed.

LOGS show some ACPI problems, but I am not sure what is causing them given that everything has been working fine, and I haven't changed any bios settings

[IMG]https://i.imgur.com/Nfoppfe.jpg[/IMG]

I tried Ubuntu 21 and the problem presisted. The problem goes away on Pop!_OS 20.04 LTS (I can restart/shutdown) without any issues, but suspend stop working on POPOS. it has been previously working on Ubuntu

---

### Post by TheFu on 2022-01-23
ACPI is often how shutdown happens.  I'd follow up on that issue.
Does booting from a prior kernel fix it?
Does booting from a "Try Ubuntu" flash drive fix it?

Seems like a kernel "regression", so it would be most helpful if you can figure out exactly which kernel releases work and which don't work.
I haven't seen the issue with 5.4.x kernels or 5.11.20-xxxx kernels on either of my Ryzen systems.  I have a 2600 and a 5600G, but I'm only using 20.04 inside virtual machines, not on real hardware.

The motherboard, BIOS, and kernel are all involved, so a table of each which do and don't have the issue would be most helpful.
I think this command will show the relevant data:
```
$ inxi -SMC
```

---

### Post by username0072 on 2022-01-23
I tried an older kernel using advanced startup options and this works

I can shutdown, restart, suspend & resume without problems

```
inxi -SMC
System:    Host: mini Kernel: 5.11.0-27-generic x86_64 bits: 64 Desktop: Gnome 3.36.9 Distro: Ubuntu 20.04.3 LTS (Focal Fossa) 
Machine:   Type: Mini-pc System: ASUSTeK product: MINIPC PN50 v: 0623 serial: <superuser/root required> 
           Mobo: ASUSTeK model: PN50 serial: <superuser/root required> UEFI: ASUSTeK v: 0623 date: 05/13/2021 
CPU:       Topology: 8-Core model: AMD Ryzen 7 4700U with Radeon Graphics bits: 64 type: MCP L2 cache: 4096 KiB 
           Speed: 1397 MHz min/max: 1400/2000 MHz Core speeds (MHz): 1: 1397 2: 1348 3: 1397 4: 1397 5: 1397 6: 1397 7: 1397 
           8: 1397 
```



This does not work. I cannot shutdown, restart, or suspend at all

```
inxi -SMC
System:    Host: mini Kernel: 5.13.0-27-generic x86_64 bits: 64 Desktop: Gnome 3.36.9 Distro: Ubuntu 20.04.3 LTS (Focal Fossa) 
Machine:   Type: Mini-pc System: ASUSTeK product: MINIPC PN50 v: 0623 serial: <superuser/root required> 
           Mobo: ASUSTeK model: PN50 serial: <superuser/root required> UEFI: ASUSTeK v: 0623 date: 05/13/2021 
CPU:       Topology: 8-Core model: AMD Ryzen 7 4700U with Radeon Graphics bits: 64 type: MCP L2 cache: 4096 KiB 
           Speed: 1397 MHz min/max: 1400/2000 MHz Core speeds (MHz): 1: 1397 2: 1397 3: 1398 4: 1396 5: 1397 6: 1397 7: 1398 
           8: 1397
```

---

### Post by username0072 on 2022-01-24
I tried kernel [COLOR=#000000]5.13.1-051301 and this works too (shutdown, restart, suspend and resume). There were a few errors during installation, but it booted fine[/COLOR]

```
inxi -SMC
System:    Host: mini Kernel: 5.13.1-051301-generic x86_64 bits: 64 Desktop: Gnome 3.36.9 
           Distro: Ubuntu 20.04.3 LTS (Focal Fossa) 
Machine:   Type: Mini-pc System: ASUSTeK product: MINIPC PN50 v: 0623 serial: <superuser/root required> 
           Mobo: ASUSTeK model: PN50 serial: <superuser/root required> UEFI: ASUSTeK v: 0623 date: 05/13/2021 
CPU:       Topology: 8-Core model: AMD Ryzen 7 4700U with Radeon Graphics bits: 64 type: MCP L2 cache: 4096 KiB 
           Speed: 1397 MHz min/max: 1400/2000 MHz Core speeds (MHz): 1: 1397 2: 1397 3: 1397 4: 1397 5: 1397 6: 1397 7: 1397 
           8: 1397 
```

---

### Post by TheFu on 2022-01-24
I think the next step is to file an official bug report: [https://wiki.ubuntu.com/Kernel/Bugs](https://wiki.ubuntu.com/Kernel/Bugs)
Looks like something got fixed between 5.13.0 and 5.13.1 in the 5.13.x kernel line (or perhaps in the 5.12.x?).

---

### Post by username0072 on 2022-01-24
> **TheFu said:**
> I think the next step is to file an official bug report: [https://wiki.ubuntu.com/Kernel/Bugs](https://wiki.ubuntu.com/Kernel/Bugs)
Looks like something got fixed between 5.13.0 and 5.13.1 in the 5.13.x kernel line (or perhaps in the 5.12.x?).


Is there something else I can do to confirm that something is broken in Kernel 5.13.0 before I file a bug report?. I am new with Linux, and I am not sure if I have covered everything before filing a bug report :-)

---

### Post by hoavo2 on 2022-01-29
I have the same issue like you there is a bug in 5.13 kernel. To solve this in boot grub menu choose "Advanced option" and boot into older kernel version, try shut down, if you can shutdown normally, that means the new kernel version has bug and not have been solved yet, you can keep boot to the old kernel to use Ubuntu or you can downgrade kernel to older version.

---

