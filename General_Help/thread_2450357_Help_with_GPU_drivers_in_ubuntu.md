---
title: "Help with GPU drivers in ubuntu"
date: 2020-09-11
forum: General Help
---

### Post by cheloxnz on 2020-09-11
Hi everybody how are you? a question, I have ubuntu in version 20.04, I wanted to know how to install the drivers for my gpu, I have an apu a6-7480 r5 series. Thank you very much.

---

### Post by Bashing-om on 2020-09-11
cheloxnz; Hello - Welcome to the forum.

What leads you to the assumption that you need to manually install a graphic's driver ?
In most cases the drivers are included in the kernel.

Post back - between code tags - the output of terminal command:
```

sudo lshw -C display

```

And we see here what story gets told - and go from there.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by TheFu on 2020-09-11
```
sudo ubuntu-drivers autoinstall
```
I think amd drivers are automatic. Intel are.  nVidia works wth the command above.

Don't go looking to manually install drivers outside the packaging system without very good reason.  There are long term ramifications.

---

### Post by QIII on 2020-09-11
At install time, if the installer detects a supported AMD GPU, the amdgpu driver will be "installed" -- actually, the existing module in the kernel will be used.  If the hardware is not supported by amdgpu, the existing radeon kernel module will be used.

You need do nothing more when installing on a machine with AMD graphices, provided it is not a hybrid graphics setup with Intel and AMD graphics hardware.  That is not supported well by the industry and the Linux developers are left to drown.  The correct AMD module is loaded, but the AMD module and the Intel module may be at odds.

Would you please use the terminal and post the results of

```
lsmod | grep amdgpu
```

and 

```
lsmod | grep radeon
```

The first queries the system to see if the amdgpu module is loaded.  The second queries the system to see if the radeon module is loaded.

lsmod lists the loaded modules.  That is piped to 'grep', which is the commend for **g**lobal **r**egular **e**xpression **p**rint.  That will list modules related to amdgpu or radeon.

---

### Post by cheloxnz on 2020-09-11
> **Bashing-om said:**
> cheloxnz; Hello - Welcome to the forum.

What leads you to the assumption that you need to manually install a graphic's driver ?
In most cases the drivers are included in the kernel.

Post back - between code tags - the output of terminal command:
```

sudo lshw -C display

```

And we see here what story gets told - and go from there.[INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]


The problem is that I have 2 monitors, in windows they worked perfectly for me, I have windows and ubuntu, I start windows and both work perfectly, I start ubuntu and only one works. One is connected by HDMI and the other VGA. And I thought maybe they flataban drivers.

> **TheFu said:**
> ```
sudo ubuntu-drivers autoinstall
```
I think amd drivers are automatic. Intel are. nVidia works wth the command above.

Don't go looking to manually install drivers outside the packaging system without very good reason. There are long term ramifications.

Yes, I thought that, but as I mentioned above, due to the non-functioning of a monitor. Thank you



> **QIII said:**
> At install time, if the installer detects a supported AMD GPU, the amdgpu driver will be "installed" -- actually, the existing module in the kernel will be used.  If the hardware is not supported by amdgpu, the existing radeon kernel module will be used.

You need do nothing more when installing on a machine with AMD graphices, provided it is not a hybrid graphics setup with Intel and AMD graphics hardware.  That is not supported well by the industry and the Linux developers are left to drown.  The correct AMD module is loaded, but the AMD module and the Intel module may be at odds.

Would you please use the terminal and post the results of

```
lsmod | grep amdgpu
```

and 

```
lsmod | grep radeon
```

The first queries the system to see if the amdgpu module is loaded.  The second queries the system to see if the radeon module is loaded.

lsmod lists the loaded modules.  That is piped to 'grep', which is the commend for **g**lobal **r**egular **e**xpression **p**rint.  That will list modules related to amdgpu or radeon.

---

### Post by TheFu on 2020-09-12
Please copy/paste text.  Don't post images.

---

### Post by cheloxnz on 2020-09-12
> **TheFu said:**
> Please copy/paste text.  Don't post images.

```
cheloxnz@chelo:~$ lsmod | grep amdgpu
amdgpu               4579328  0
amd_iommu_v2           20480  1 amdgpu
gpu_sched              32768  1 amdgpu
ttm                   106496  1 amdgpu
drm_kms_helper        184320  1 amdgpu
i2c_algo_bit           16384  1 amdgpu
drm                   491520  4 gpu_sched,drm_kms_helper,amdgpu,ttm
cheloxnz@chelo:~$ lsmod | grep radeon
cheloxnz@chelo:~$ 

```

---

### Post by TheFu on 2020-09-12
And the other requested command outputs?

---

### Post by cheloxnz on 2020-09-12
> **TheFu said:**
> And the other requested command outputs?

Yes.
```

cheloxnz@chelo:~$ sudo lshw -C display
[sudo] password for cheloxnz: 
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: Wani [Radeon R5/R6/R7 Graphics]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: e6
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller cap_list
       configuration: latency=0
       resources: memory:c0000000-cfffffff memory:d0000000-d07fffff ioport:f000(size=256) memory:feb00000-feb3ffff memory:c0000-dffff
cheloxnz@chelo:~$ sudo ubuntu-drivers autoinstall
No drivers found for installation.
cheloxnz@chelo:~$ 

```

---

### Post by TheFu on 2020-09-12
Sorry, I don't have any systems with AMD GPUs, but 

nvidia ($70):
```
$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: GP108 [GeForce GT 1030]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: **[COLOR="#FF0000"]driver=nvidia[/COLOR]** latency=0
       resources: irq:85 memory:f5000000-f5ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff
```

nvidia 430 GT that is failing. It has been dying a few months. Think it was $30 about 9-10 yrs ago.
```
           *-generic:0
                description: Unassigned class
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 0
                bus info: pci@0000:01:00.0
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list rom
                configuration: **[COLOR="#FF0000"]driver=nvidia[/COLOR]** latency=255 maxlatency=255 mingnt=255
                resources: irq:16 memory:fa000000-faffffff memory:d8000000-dfffffff memory:d6000000-d7ffffff ioport:ac00(size=128) memory:c0000-dffff
```

KVM/QEMU Virtual Machine:
```
$ sudo lshw -C display
  *-display                 
       description: VGA compatible controller
       product: QXL paravirtual graphic card
       vendor: Red Hat, Inc.
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller rom
       configuration: **[COLOR="#FF0000"]driver=qxl[/COLOR]** latency=0
       resources: irq:10 memory:f4000000-f7ffffff memory:f8000000-fbffffff memory:fc058000-fc059fff ioport:c0c0(size=32) memory:c0000-dffff
```

Intel iGPU from Pentium G3258 CPU ($50 new):```

$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: **[COLOR="#FF0000"]driver=i915[/COLOR]** latency=0
       resources: irq:29 memory:f7400000-f77fffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff
```

The fact that no driver is being shown for the AMD on your system is concerning.  Need to wait for someone with an AMD GPU to respond, it seems. Sorry.

---

### Post by cheloxnz on 2020-09-12
> **TheFu said:**
> Sorry, I don't have any systems with AMD GPUs, but 

nvidia ($70):
```
$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: GP108 [GeForce GT 1030]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: **[COLOR=#FF0000]driver=nvidia[/COLOR]** latency=0
       resources: irq:85 memory:f5000000-f5ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff
```

nvidia 430 GT that is failing. It has been dying a few months. Think it was $30 about 9-10 yrs ago.
```
           *-generic:0
                description: Unassigned class
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 0
                bus info: pci@0000:01:00.0
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list rom
                configuration: **[COLOR=#FF0000]driver=nvidia[/COLOR]** latency=255 maxlatency=255 mingnt=255
                resources: irq:16 memory:fa000000-faffffff memory:d8000000-dfffffff memory:d6000000-d7ffffff ioport:ac00(size=128) memory:c0000-dffff
```

KVM/QEMU Virtual Machine:
```
$ sudo lshw -C display
  *-display                 
       description: VGA compatible controller
       product: QXL paravirtual graphic card
       vendor: Red Hat, Inc.
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller rom
       configuration: **[COLOR=#FF0000]driver=qxl[/COLOR]** latency=0
       resources: irq:10 memory:f4000000-f7ffffff memory:f8000000-fbffffff memory:fc058000-fc059fff ioport:c0c0(size=32) memory:c0000-dffff
```

Intel iGPU from Pentium G3258 CPU ($50 new):```

$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: **[COLOR=#FF0000]driver=i915[/COLOR]** latency=0
       resources: irq:29 memory:f7400000-f77fffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff
```

The fact that no driver is being shown for the AMD on your system is concerning.  Need to wait for someone with an AMD GPU to respond, it seems. Sorry.

Is that why I can't use 2 screens? I also do not understand, from what it says there I understand that it recognizes my driver, but honestly I am not understanding.

---

### Post by TheFu on 2020-09-12
This is yours: ```

$ sudo lshw -C display
[sudo] password for cheloxnz: 
  *-display **[COLOR="#FF0000"]UNCLAIMED       [/COLOR]**
       description: VGA compatible controller
       product: Wani [Radeon R5/R6/R7 Graphics]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: e6
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller cap_list
       [COLOR="#FF0000"][B]configuration: latency=0
[/B][/COLOR]       resources: memory:c0000000-cfffffff memory:d0000000-d07fffff ioport:f000(size=256) memory:feb00000-feb3ffff memory:c0000-dffff
```
The card is "unclamed" and doesn't show any driver.  That's sorta important.  Look at the "configuration:" lines for all my GPUs.  They list the driver .... I **bold**ed and made it [COLOR="#FF0000"]RED[/COLOR] in hope that it would jump out to you.

A driver is being loaded - lsmod shows that - but it doesn't seem to recognize the GPU.  There are a few choices, at least that I can guess.
a) the wrong driver was loaded.
b) the card is failing in some way.
c) the card is reporting it is initialized already, but isn't.  This can happen on dual-boot systems with Windows if Windows OS isn't fully, completely, powered off.  5 yrs ago, some hardware, not GPUs, needed Windows to initialize the hardware before it would work. The vendor had created really bad drivers for Linux that didn't initialize all the registers correctly, so when power was lost, whatever the power-spike caused put *something random* into those registers.  Almost always, it was incorrect values, but once every 50 boots, it would work. Some of that old hardware is certainly still in the world.  Again, it wasn't GPUs, so that really shouldn't matter here.

For me, I'd swap in an old GPU I have laying around and see if that changes things. I have a few PCI, AGP, and PCIe GPUs laying around for that still.

And just so it is clear - I probably will not buy another nvidia GPU for my next systems.  The driver hassles with those are more than I care to deal with anymore. My next build will probably be a Ryzen 2xxx after the next generation has been available for a few months and prices drop 30-50%.

---

### Post by cheloxnz on 2020-09-13
> **cheloxnz said:**
> Is that why I can't use 2 screens? I also do not understand, from what it says there I understand that it recognizes my driver, but honestly I am not understanding.

So linux does not serve me any distribution, unfortunately I have to use windows, it works much better with linux.
Thanks greetings.

---

