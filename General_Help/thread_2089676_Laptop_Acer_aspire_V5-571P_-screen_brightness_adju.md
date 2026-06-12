---
title: "Laptop Acer aspire V5-571P -screen brightness adjustment not working with fn+ keys"
date: 2012-11-29
forum: General Help
---

### Post by lvgandhi on 2012-11-29
My laptop is having multi boot with windows 8, lubuntu 12.04, kubuntu 12.04 and mint maya. In none of them  except in windows 8, I could reduce/increase brightness.

I have gone through many posts and did google search.
Details asked by many are same and given below
lvgandhi@lvgandhi-Aspire-V5-571P:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-33-generic root=UUID=da4a4f7d-5e47-4a94-a914-3ec0c249b7c3 ro acpi_os_name=Microsoft Windows XP quiet splash vt.handoff=7

lvgandhi@lvgandhi-Aspire-V5-571P:~$ ls /sys/class/backlight/*/
/sys/class/backlight/acpi_video0/:
actual_brightness  bl_power  brightness  device  max_brightness  power  subsystem  type  uevent

/sys/class/backlight/intel_backlight/:
actual_brightness  bl_power  brightness  device  max_brightness  power  subsystem  type  uevent

lvgandhi@lvgandhi-Aspire-V5-571P:~$ sudo lspci -vnn | grep -A10 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Ivy Bridge Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device [1025:072d]
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 3000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: i915

I  tried grub options
acpi_osi=Linux acpi_backlight=vendor
acpi_osi=Linux 
these don't work.

acpi_os_name="Microsoft Windows XP"
With last option, update grub does not work. I get error msg as"/usr/sbin/grub-mkconfig: 12: /etc/default/grub: Windows: not found"

I request help in controlling brightness in my laptop.

---

### Post by HeWhoE on 2013-04-30
Bumpity-bump.

---

