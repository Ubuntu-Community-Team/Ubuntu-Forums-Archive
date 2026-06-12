---
title: "Cannot select additional (graphic) driver"
date: 2015-04-16
forum: General Help
---

### Post by azzach19 on 2015-04-16
Hello, yesterday I was able to fix an issue regarding my graphics driver in [this thread]("http://ubuntuforums.org/showthread.php?t=2273776"). Today I'm looking to get back to my old driver that I was using which has support for OpenGL 4.2. Basically, when I go to "Software & Updates" -> "Additional Drivers" settings I can only select "continue using a manually installed driver," but I want to use fglrx. I added an image of what the driver screen looks like on my end in the attachments.

Here's some output related to my drivers that might be helpful:
```

zeep@zeep-computer:~$ glxinfo | grep "OpenGL" 
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits)
OpenGL version string: 2.1 Mesa 10.1.3
OpenGL shading language version string: 1.30
OpenGL extensions:

```

```
zeep@zeep-computer:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: Cape Verde PRO [Radeon HD 7750 / R7 250E]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:16 memory:e0000000-efffffff memory:f7e00000-f7e3ffff ioport:e000(size=256) memory:f7e40000-f7e5ffff
```

---

### Post by QIII on 2015-04-16
Which version and point release of Ubuntu are you using?

Please post back the results of
```
 lsb_release -a 
```

This is important due to an outstanding bug in the fglrx installer.

---

### Post by azzach19 on 2015-04-16
I have:
```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

```

---

### Post by QIII on 2015-04-16
OK.  The fglrx choices are disabled because the installer is broken.

Please have a read through [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491)

If you are comfortable using the installer in trusty-proposed, see my post #77.

Otherwise wait a few days for it to hit the Trusty repo.

---

### Post by azzach19 on 2015-04-16
OK, will do and thanks for the feedback.

---

