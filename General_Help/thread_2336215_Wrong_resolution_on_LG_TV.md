---
title: "Wrong resolution on LG TV"
date: 2016-09-06
forum: General Help
---

### Post by duduamar on 2016-09-06
Hey
I have just installed Ubuntu desktop 16.04.1 on my Intel NUC connected to LG TV 60".
My issue is the resolution is not properly set - the detected screen is bigger than the actual TV, so for example the unity bar is cropped (I see only half of it).
I looked at "Screen Display" settings and the resolution set there is 1080p, but even after changing to 4K (my TV supports that), the bar is still cropped (and anyway it's too small for me).
My detected TV in the settings is "Goldstar 72", I understand that LG == Goldstar, but why the 72" instead of 60" ?

Any ideas how to fix that?

Thanks.

---

### Post by Bucky Ball on 2016-09-06
Welcome. Open 'Additional Drivers'. Do you see a driver for your video card there that is disabled? Confirm which here before enabling. 

Please open a terminal and copy/paste this in and hit enter.

```
sudo lshw -C video
```

Post the output here between code tags, please (see the link in my signature below for how to use them).

---

### Post by SeijiSensei on 2016-09-06
On your LG remote, press the "Ratio" button and choose "Just Scan" instead of 16:9 or other settings. You can also do this from the Settings menu under Picture > Aspect Ratio.

---

### Post by duduamar on 2016-09-06
Thanks Bucky Ball.

In Additional Drivers I see this:
```

Unknown: Unknown
This device is using an alternative driver
- Using Processor microcode firmware for Intel CPUs from intel-microcode (proprietary)
- Do not use the device

```

The output of lshw command:
```

* - display
description: VGA compatible controller
product: Broadwell-U Integrated Graphics
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 09
width: 64 bits
clock: 33 Mhz
capabilities: msi pm vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0 
resources: irq:45 memory:a9000000-a9ffffff memory:b0000000-bfffffff iopor:3000(size=64)

```

Hope that tells you something :)

---

### Post by duduamar on 2016-09-07
> **SeijiSensei said:**
> On your LG remote, press the "Ratio" button and choose "Just Scan" instead of 16:9 or other settings. You can also do this from the Settings menu under Picture > Aspect Ratio.

Thanks, that solved it!

---

