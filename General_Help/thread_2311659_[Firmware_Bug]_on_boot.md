---
title: "[Firmware Bug] on boot"
date: 2016-01-29
forum: General Help
---

### Post by sey2 on 2016-01-29
Hey guys,

When I turn my laptop(Asus Aspire E15), with "Ubuntu Gnome", on there is a message, before the whole system starts after a delay
```

[Firmware Bug]: cpu 0, invalid threshold interrupt offset 0 for bank 4, block 1 (MSRC0000408=0xc010000001000000)
Ignoring BGRT: invalid status 0(expected 1)
[Firmware Bug]: cpu 1, try to use APIC500 (LVT offset 0) for vect or 0x10400, but the register is already in use for vector 0xf9 on another cpu
[Firmware Bug]: cpu 1, IBS interrupt offset 0 not available (MSRC001103A=0x0000000000000100)
Failed to setup IBS, -22
kfd kfd: error getting iommu info. is the iommu enabled?
kfd kfd: error initializing iommuv2 for device (1002:1309)
kfd kfd: device (1002:1309) NOT added due to errors
radeon 0000:01:00.0: VCE init error(-110)
[drm:radeon_acpi_init [radeon]] *ERROR* Cannot find the backlight controler fsck from util-linux 2.26.2
/dev/sda2: clean 223755/60563456 files, 5394458/242237952 blocks

```(There were timestamps before each line, but I let them out)

And after that everything is back to normal, I can login normally and do whatever I want to, but not knowing what that is and that it appears every time worries me

I am pretty new to Linux and stuff like this is new to me, since I never had to confront with problems like this.
I hope anybody can help me, thanks you very very much in advance.

---

