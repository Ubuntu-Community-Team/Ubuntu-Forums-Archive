---
title: "Window boarders distorted"
date: 2014-03-05
forum: General Help
---

### Post by childintime on 2014-03-05
Hello, I've got a problem for a few days that my window boarders look distorted. 

For example that's how LibreOffice window looks over gmail website: [http://i.imgur.com/cadsL0f.png](http://i.imgur.com/cadsL0f.png)

That's Skype over Ubuntu forums: [http://i.imgur.com/MCkwWQ2.png](http://i.imgur.com/MCkwWQ2.png)

Any idea how to fix that? :eek:

By the way, I tried changing to different window styles in options but it does not help.

---

### Post by ajgreeny on 2014-03-05
Looks like a graphics card/driver glitch to me; what card and driver do you have running?

---

### Post by childintime on 2014-03-06
> **ajgreeny said:**
> Looks like a graphics card/driver glitch to me; what card and driver do you have running?

card nvidia geforce 740M
driver=nouveau

```
mosquito@mosquito-K56CB:~$ modinfo nouveaufilename:       /lib/modules/3.11.0-17-generic/kernel/drivers/gpu/drm/nouveau/nouveau.ko
license:        GPL and additional rights
description:    nVidia Riva/TNT/GeForce/Quadro/Tesla
author:         Nouveau Project
srcversion:     2993D20E3786D049DABE172
alias:          pci:v000012D2d*sv*sd*bc03sc*i*
alias:          pci:v000010DEd*sv*sd*bc03sc*i*
depends:        drm,drm_kms_helper,ttm,mxm-wmi,wmi,video,i2c-algo-bit
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 
parm:           perflvl:Performance level (default: boot) (charp)
parm:           perflvl_wr:Allow perflvl changes (warning: dangerous!) (int)
parm:           tv_norm:Default TV norm.
        Supported: PAL, PAL-M, PAL-N, PAL-Nc, NTSC-M, NTSC-J,
            hd480i, hd480p, hd576i, hd576p, hd720p, hd1080i.
        Default: PAL
        *NOTE* Ignored for cards with external TV encoders. (charp)
parm:           tv_disable:Disable TV-out detection (int)
parm:           ignorelid:Ignore ACPI lid status (int)
parm:           duallink:Allow dual-link TMDS (default: enabled) (int)
parm:           nofbaccel:Disable fbcon acceleration (int)
parm:           agpmode:AGP mode (0 to disable AGP) (int)
parm:           vram_pushbuf:Create DMA push buffers in VRAM (int)
parm:           config:option string to pass to driver core (charp)
parm:           debug:debug string to pass to driver core (charp)
parm:           noaccel:disable kernel/abi16 acceleration (int)
parm:           modeset:enable driver (default: auto, 0 = disabled, 1 = enabled, 2 = headless) (int)



```

---

### Post by ajgreeny on 2014-03-06
That is the open source driver, I think, so you may do better if you go to **Additional Drivers** and install the recommended proprietary one from there.

I don't have any nvidia hardware, so I may be wrong about this, so a wait for other replies is probably worthwhile.

---

### Post by childintime on 2014-03-07
> **ajgreeny said:**
> That is the open source driver, I think, so you may do better if you go to **Additional Drivers** and install the recommended proprietary one from there.

I don't have any nvidia hardware, so I may be wrong about this, so a wait for other replies is probably worthwhile.

I installed that driver, and after reboot and login I get black screen. I tried many different solutions posted on askubuntu but nothing worked for me. I created new thread for this as well: [http://ubuntuforums.org/showthread.php?t=2209844&p=12950030#post12950030](http://ubuntuforums.org/showthread.php?t=2209844&p=12950030#post12950030)

---

