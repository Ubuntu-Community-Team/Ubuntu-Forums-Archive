---
title: "Ubuntu 22.10 / Kernel 5.19 changed video outputs enumeration ?"
date: 2022-11-04
forum: General Help
---

### Post by saroumane2 on 2022-11-04
Switching from kernel 5.15.x (Ubuntu 22.04) to current kernel 5.19.0 from Ubuntu 22.10, I found that kernel video outputs enumeration has changed.
I have 2 HDMI outputs on the 1st graphics card, 1 HDMI output on the 2nd graphics card.
They are seen by xrandr as :
```
HDMI-A-1
HDMI-A-2
HDMI-2-1 

```
Only one is physically plugged : **HDMI-A-2**

This is my grub config : ```
GRUB_CMDLINE_LINUX_DEFAULT="video=HDMI-A-2:640x480D drm.edid_firmware=HDMI-A-2:edid/640x480p60.bin"
```

With kernel **5.15.76**, after boot I get this with **xrandr** :```
HDMI-A-1 disconnected (normal left inverted right x axis y axis)
HDMI-A-2 connected (normal left inverted right x axis y axis)
640x480       59.94 +*
HDMI-2-1 disconnected (normal left inverted right x axis y axis)
```

With kernel **5.19.0-23-generic** after boot I get this with **xrandr** :
```
HDMI-A-1 connected (normal left inverted right x axis y axis)
640x480       59.94 +*
HDMI-A-2 disconnected (normal left inverted right x axis y axis)
HDMI-2-1 disconnected (normal left inverted right x axis y axis)
```

To keep my setup working I had to modify my grub config by "adding 1", like this :
```
GRUB_CMDLINE_LINUX_DEFAULT="video=HDMI-A-3:640x480D drm.edid_firmware=HDMI-A-3:edid/640x480p60.bin"
```

Question : does anyone know if it's a temporary change that will be reverted, or the new way used by the kernel to enumerate video outputs ?

---

