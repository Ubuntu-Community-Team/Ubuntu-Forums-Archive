---
title: "freezeing after grub booting ubuntu"
date: 2018-09-14
forum: General Help
---

### Post by kuraiskrap on 2018-09-14
Dell inspiron 5575
2500u ryzen

Gnome 3.28.2

newest Ubuntu

tried reinstalling

boots into grub fine
boots into windows 10 with no issues
sometimes it boots sometime it freezes and needs a hard reset
new to linux, just wondering if anyone had any ideas?


i have a few logs

successful boot log

tgn10_lock line:566
08:49:57 systemd-rfkill: Failed to open device rfkill3: No such device
08:49:50 wpa_supplicant: dbus: Failed to construct signal
08:49:50 kernel: Bluetooth: hci0: Failed to send firmware data (-38)
08:49:49 systemd-rfkill: Failed to open device rfkill2: No such device
08:49:49 kernel: [drm:generic_reg_wait [amdgpu]] *ERROR* REG_WAIT timeout 1us * 100 tries - tgn10_lock line:566
08:28:21 systemd-rfkill: Failed to open device rfkill0: No such device
08:28:18 spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
08:28:17 pulseaudio: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
08:28:15 wpa_supplicant: dbus: Failed to construct signal
08:28:14 kernel: [drm:generic_reg_wait [amdgpu]] *ERROR* REG_WAIT timeout 1us * 100 tries - tgn10_lock line:566
08:28:14 kernel: Bluetooth: hci0: Failed to send firmware data (-38)
08:28:13 kernel: AMD-Vi: Unable to write to IOMMU perf counter.
08:28:13 kernel: [Firmware Bug]: AMD-Vi: No southbridge IOAPIC found

Crash log 1
08:25:08 kernel: [TTM] Memory type 2 has not been initialized
08:25:08 kernel: amdgpu 0000:03:00.0: Fatal error during GPU init
08:25:08 kernel: [drm:amdgpu_get_bios [amdgpu]] *ERROR* Unable to locate a BIOS ROM
08:25:08 kernel: amdgpu 0000:03:00.0: Invalid PCI ROM header signature: expecting 0xaa55, got 0xffff
08:25:08 kernel: AMD-Vi: Unable to write to IOMMU perf counter.
08:25:08 kernel: [Firmware Bug]: AMD-Vi: No southbridge IOAPIC found

Crash log 2
08:26:50 systemd-rfkill: Failed to open device rfkill0: No such device
08:26:47 spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
08:26:44 wpa_supplicant: dbus: Failed to construct signal
08:26:43 kernel: Bluetooth: hci0: Failed to send firmware data (-38)
08:26:42 kernel: [TTM] Memory type 2 has not been initialized
08:26:42 kernel: amdgpu 0000:03:00.0: Fatal error during GPU init
08:26:42 kernel: [drm:amdgpu_get_bios [amdgpu]] *ERROR* Unable to locate a BIOS ROM
08:26:42 kernel: amdgpu 0000:03:00.0: Invalid PCI ROM header signature: expecting 0xaa55, got 0xffff
08:26:42 kernel: AMD-Vi: Unable to write to IOMMU perf counter.
08:26:42 kernel: [Firmware Bug]: AMD-Vi: No southbridge IOAPIC found

---

