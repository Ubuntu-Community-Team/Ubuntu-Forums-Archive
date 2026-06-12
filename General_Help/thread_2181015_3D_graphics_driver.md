---
title: "3D graphics driver"
date: 2013-10-15
forum: General Help
---

### Post by Keith_Valin on 2013-10-15
Does anyone know of a stable 3D graphics driver?

---

### Post by QIII on 2013-10-15
Hello!

For which manufacturer?  Drivers are specific to the manufacturer of the card, and some models have specific drivers under that.

The open source default drivers for NVIDIA and ATI (which are used on installation) handle 3D, depending on the model of the card.

The proprietary drivers for each handle 3D, again depending on the model of the card.

---

### Post by Keith_Valin on 2013-10-20
No clue for which manufacturer.  Tried a property driver under "Additional Drivers" in the settings menu, but that made my computer freeze a lot and made my connection slower, so want to avoid that.

---

### Post by QIII on 2013-10-20
What version of Ubuntu are you using?

Could you please run

```
sudo lshw -C video
```

in the terminal and post back the results?

(To copy text from the terminal, highlight it and press CTRL+SHIFT+C)

---

### Post by Keith_Valin on 2013-10-21
```

*-display               
       description: VGA compatible controller
       product: Kabini [Radeon HD 8330]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:77 memory:e0000000-efffffff memory:f0800000-f0ffffff ioport:4000(size=256) memory:f0200000-f023ffff memory:f0260000-f027ffff 
```
is what it gave me.
using 12.04 LTS

---

### Post by Yellow Pasque on 2013-10-21
It's a fairly new device, so running a more recent version of Ubuntu (13.10) would be best.
If you wanted to use the open source driver, you would need the KABINI firmware files (place them in /lib/firmware/radeon): [http://people.freedesktop.org/~agd5f/radeon_ucode/](http://people.freedesktop.org/~agd5f/radeon_ucode/)
Even then, I don't think 3D would work well.

As for proprietary driver, see instructions here: [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL)
They should work, except you may have to use --buildpkg Ubuntu/precise (I'm still a bit confused with the LTS enablements stacks).

---

