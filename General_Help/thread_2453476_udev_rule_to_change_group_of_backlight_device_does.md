---
title: "udev rule to change group of backlight device does not work"
date: 2020-11-11
forum: General Help
---

### Post by cunfusu on 2020-11-11
Hi
I'm running ubuntu 20.04 and i3 as window manager.
I'm trying to change group owner of the backlight device to video (of which my user is part of) so that I can change the brightness without need of using sudo

```
&#10140;  ~ cat /etc/udev/rules.d/95-backlight.rules
ACTION=="add", SUBSYSTEM=="backlight", KERNEL=="intel_backlight", GROUP="video", MODE="0664"
```

this is what I get when I run udevadm info on the path.

```
&#10140;  ~    udevadm info --attribute-walk --path=/sys/class/backlight/intel_backlight

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight':
    KERNEL=="intel_backlight"
    SUBSYSTEM=="backlight"
    DRIVER==""
    ATTR{brightness}=="6000"
    ATTR{max_brightness}=="120000"
    ATTR{actual_brightness}=="6000"
    ATTR{bl_power}=="0"
    ATTR{type}=="raw"
    ATTR{scale}=="unknown"

  looking at parent device '/devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1':
    KERNELS=="card0-eDP-1"
    SUBSYSTEMS=="drm"
    DRIVERS==""
    ATTRS{enabled}=="enabled"
    ATTRS{status}=="connected"
    ATTRS{edid}==""
    ATTRS{dpms}=="On"

  looking at parent device '/devices/pci0000:00/0000:00:02.0/drm/card0':
    KERNELS=="card0"
    SUBSYSTEMS=="drm"
    DRIVERS==""
    ATTRS{gt_act_freq_mhz}=="350"
    ATTRS{gt_max_freq_mhz}=="1150"
    ATTRS{gt_RP0_freq_mhz}=="1150"
    ATTRS{gt_RPn_freq_mhz}=="350"
    ATTRS{gt_min_freq_mhz}=="350"
    ATTRS{gt_cur_freq_mhz}=="350"
    ATTRS{gt_boost_freq_mhz}=="1150"
    ATTRS{gt_RP1_freq_mhz}=="350"

  looking at parent device '/devices/pci0000:00/0000:00:02.0':
    KERNELS=="0000:00:02.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="i915"
    ATTRS{max_link_width}=="255"
    ATTRS{broken_parity_status}=="0"
    ATTRS{device}=="0x9bc4"
    ATTRS{vendor}=="0x8086"
    ATTRS{dma_mask_bits}=="39"
    ATTRS{local_cpus}=="fff"
    ATTRS{consistent_dma_mask_bits}=="39"
    ATTRS{msi_bus}=="1"
    ATTRS{subsystem_device}=="0x097d"
    ATTRS{subsystem_vendor}=="0x1028"
    ATTRS{boot_vga}=="1"
    ATTRS{current_link_width}=="0"
    ATTRS{current_link_speed}=="Unknown speed"
    ATTRS{driver_override}=="(null)"
    ATTRS{d3cold_allowed}=="1"
    ATTRS{enable}=="1"
    ATTRS{irq}=="150"
    ATTRS{ari_enabled}=="0"
    ATTRS{numa_node}=="-1"
    ATTRS{revision}=="0x05"
    ATTRS{class}=="0x030000"
    ATTRS{local_cpulist}=="0-11"
    ATTRS{max_link_speed}=="Unknown speed"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""


```

I've adapted the rule from this [arch wiki]("https://wiki.archlinux.org/index.php/Backlight#ACPI") section.
the difference is the KERNEL match because mine is different. In general it seems correct to me. 
Unfortunatelly it does not seem to have any effect.
I've tried to reboot many times but the owner and permission of the device remain the same.

Am I doing something wrong?

as you can see the group is still root.
```
&#10140;  ~ ls -l /sys/class/backlight/intel_backlight 
lrwxrwxrwx 1 root root 0 Nov 11 14:51 /sys/class/backlight/intel_backlight -> ../../devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight
```

---

