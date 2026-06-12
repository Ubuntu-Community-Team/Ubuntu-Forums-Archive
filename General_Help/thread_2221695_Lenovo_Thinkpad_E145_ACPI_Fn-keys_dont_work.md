---
title: "Lenovo Thinkpad E145 ACPI Fn-keys dont work"
date: 2014-05-03
forum: General Help
---

### Post by pacmyc1 on 2014-05-03
I can't get the Fn-keys to work on this system.

The Fn-keys for mute, vol-, vol+, change video mode, brightness-, brightness+, prev, pause/play, next, wifi on/off
all gives output when I run acpi_listen.

The key to control brightness triggers the on screen menu, and changes it as the buttons are pressed, but the brightness is not being changed.

The other Fn-keys do not trigger anyhting, except for the output when running acpi_listen.

```
 
dmesg | grep acpi/
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=0aa0c3fb-378f-4bf2-a5a4-58f063764777 ro acpi_os=Linux quiet splash acpi_backlight=vendor vt.handoff=7
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=0aa0c3fb-378f-4bf2-a5a4-58f063764777 ro acpi_os=Linux quiet splash acpi_backlight=vendor vt.handoff=7
[    0.273991] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.325562] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.325877] acpi PNP0A08:00: _OSC: platform does not support [PME]
[    0.326181] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug AER PCIeCapability]
[    0.328177] acpi PNP0A08:00: ignoring host bridge window [mem 0x000ce000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000ce9ff])
[    0.328189] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.360197] Found 1 acpi root devices
[    0.999645] ACPI: acpi_idle registered with cpuidle
[    1.203109] acpi-cpufreq: overriding BIOS provided _PSD data
[   13.095415] thinkpad_acpi: ThinkPad ACPI Extras v0.25
[   13.095420] thinkpad_acpi: http://ibm-acpi.sf.net/
[   13.095423] thinkpad_acpi: ThinkPad BIOS HSET56WW (2.01 ), EC unknown
[   13.095427] thinkpad_acpi: Lenovo ThinkPad Edge E145, model 20BC000UMS
[   13.101636] thinkpad_acpi: Unsupported brightness interface, please contact ibm-acpi-devel@lists.sourceforge.net
[   13.108782] thinkpad_acpi: radio switch found; radios are enabled
[   13.108813] thinkpad_acpi: possible tablet mode switch found; ThinkPad in laptop mode
[   13.247852] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[   13.261126] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   13.333591] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input9

```


I've been testing editing the arguments in /etc/default/grub file but without results.

---

### Post by joe116 on 2014-07-04
A little late to the party but...  I have the same notebook (Edge E145, E1-2500) and can confirm that at least the Fn-keys for regulating the brightness are not working (open and proprietary driver). A notification pops up but nothing really happens.    However, concerning the volume and wifi keys, they are actually working. I'm on Archlinux myself and the volume keys are not working. But this may very well have something to do with missing configuration.  I've booted the laptop using both, current Linux Mint and Manjaro and the volume keys were working there out of the box. They both use pulseaudio (which I don't on my Arch system) and I reckon with some configuration the volume keys can successfully be set up.    The wifi key is working out of the box on my system, no further configuration needed.    You may want to check some other distributions for their configuration.

---

