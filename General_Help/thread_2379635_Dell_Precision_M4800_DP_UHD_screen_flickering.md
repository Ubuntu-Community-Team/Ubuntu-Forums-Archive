---
title: "Dell Precision M4800 DP UHD screen flickering"
date: 2017-12-07
forum: General Help
---

### Post by inkinen on 2017-12-07
Hi,

I just installed lubuntu 17.10 on a Dell Inspiron m4800. It works fine except for then using a external 4k/uhd monitor connected display port 1 via docking bay.

The m4800 is equipped with a Intel 4600 gpu + nvidia K1100M. 4k/uhd/3840x2160 works fine when running windows but not in lubuntu unfortunately. I get flickering screen and wierd artifacts on the big 4k display ( Dell p2715q ).

I also have another display connected on dvi port 2 which runs at regular hd (1080) resolution, and this works fine. Its just the 4k output that doesnt work. 
I have tried a bunch of different nvidia drivers ( both ones availabe in Additional Driver as well as the latest from nvidias webpage ) but to no avail.
Currently using nvidia driver 340.104

Any clues?

here is what lshw says : 
```

         product: Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:e000(size=4096) memory:f4000000-f50fffff ioport:e0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GK107GLM [Quadro K1100M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:34 memory:f4000000-f4ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f5000000-f507ffff
        *-display
             description: VGA compatible controller
             product: 4th Gen Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:29 memory:f5400000-f57fffff memory:d0000000-dfffffff ioport:f000(size=64) memory:c0000-dffff

```

nvidia-smi : 
```

Thu Dec  7 21:39:19 2017       
+------------------------------------------------------+                       
| NVIDIA-SMI 340.104    Driver Version: 340.104        |                       
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  Quadro K1100M       Off  | 0000:01:00.0     Off |                  N/A |
| N/A   43C    P0    N/A /  N/A |    208MiB /  2047MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Compute processes:                                               GPU Memory |
|  GPU       PID  Process name                                     Usage      |
|=============================================================================|
|  No running compute processes found                                         |
+-----------------------------------------------------------------------------+

```

uname -a : 
```

Linux 4.13.0-17-generic #20-Ubuntu SMP Mon Nov 6 10:04:08 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by inkinen on 2017-12-07
recorded a short video of how it looks : [https://youtu.be/ESTAED7AfRw](https://youtu.be/ESTAED7AfRw)

---

### Post by inkinen on 2017-12-08
I think I managed to solve it by connecting the mDP cable to the docking bays second display port output! Had to restart Xorg also.

---

