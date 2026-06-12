---
title: "32” 4K screen on the laptop. Scaling does not work."
date: 2024-08-19
forum: General Help
---

### Post by baldrianforte on 2024-08-19
Hello, 

as indicated in the title, the font on the screen in all programs is too small and barely legible. I would like to keep the resolution of 3840x2160 for the sake of sharpness. I would therefore like to set the scaling to 125% or 150%. But only 100%, 200% are possible. Such errors are said to occur more frequently after switching from XServer to Wayland. But even the change in the file “/etc/gdm3/custom.conf” does not help if you remove the hash at “#WaylandEnable=false”.


If I scale to 125%, then it scales beyond the screen. I only have the option of “xrandr --output HDMI-1-0 --scale 1.25”. This means that the right and bottom edges of the screen disappear into nothingness due to the enlargement. 


This is not a problem under Windows. I simply enter 150% for scaling and everything is slightly larger and still remains completely visible on the screen.


**What can I do to achieve the same effect?**


My current configuration is:

```

bf@bf-pc:~$ lspci -nnk | grep -A3 "\[03..\]:"
00:02.0 VGA compatible controller [0300]: **Intel Corporation TigerLake-H GT1 **[UHD Graphics] [8086:9a60] (rev 01)
	DeviceName: Onboard - Video
	Subsystem: Micro-Star International Co., Ltd. [MSI] TigerLake-H GT1 [UHD Graphics] [1462:12e9]
	Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: **NVIDIA Corporation GA104M [GeForce RTX 3070 Mobile / Max-Q**] [10de:249d] (rev a1)
	Subsystem: Micro-Star International Co., Ltd. [MSI] GA104M [GeForce RTX 3070 Mobile / Max-Q] [1462:12e9]
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

```

Ubuntu is freshly installed. Therefore, nothing has been changed in the configuration files.

---

