---
title: "New Radeon Graphics with Ubuntu"
date: 2020-12-03
forum: General Help
---

### Post by hiker-guy on 2020-12-03
Hi all

I have got a new Thinkpad with a AMD Ryzen 7 processor and Radeon graphics. I have successfully installed Ubuntu 20.04 on it alongside Windows however Ubuntu does not recognise the display, it shows 'Unknown display' in the settings and I can not change the screen resolution. First I tried editing /etc/default/grub in various ways recommended on forums, such as adding: ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amdgpu.exp_hw_support=1"
```… but that did not work.

Then I tried installing the driver released by AMD (below) but that failed towards the end of the install with a couple of error messages.
[https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-20](https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-20)

I then found people saying that this driver released by AMD is unnecessary and that the Ubuntu kernel 5.7 upwards has inbuilt functionality to handle this. As 20.04 uses kernel 5.4 so I upgraded my Ubuntu to 20.10 so it is using kernel 5.8 but it still doesn't recognise the display. I feel like this is perhaps the solution but am I missing something obvious? 

Is there a different Linux distribution that will recognise the display?

I have also tried installing 18.04 but that did not work either.

All I want to do is change the screen resolution.

Any help would be greatly appreciated.

---

### Post by DuckHook on 2020-12-03
Welcome to the forums hiker-guy

Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

Please also refrain from using non&#8209;standard fonts and styles. This makes output difficult to read and especially destroys the formatting in code output.

I have gone ahead and edited your output to make it easier to read.

---

### Post by hiker-guy on 2020-12-04
Thank you DuckHook

---

### Post by GhX6GZMB on 2020-12-04
I can recommend installing the oibaf PPA, which is very good for keeping your graphic drivers updated:

```
sudo add-apt-repository ppa:oibaf/graphics-drivers
sudo apt-get update
```

[https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

---

### Post by hiker-guy on 2020-12-04
Thanks for the suggestion ml9104, I tired it but unfortunately it does not solve my problem. If I try this command to list the driver:
```
sudo lshw -c video
```

I get this response:

```
*-display UNCLAIMED       
       description: VGA compatible controller
       product: Renoir
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:06:00.0
       version: d1
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix vga_controller bus_master cap_list
       configuration: latency=0
       resources: iomemory:40-3f iomemory:40-3f memory:460000000-46fffffff memory:470000000-4701fffff ioport:1000(size=256) memory:fd300000-fd37ffff

```

---

### Post by QIII on 2020-12-04
I don't know what state your machine may be in, but let me first explain something:  the amdgpu and radeon modules exist in the Linux kernel.  At install time, the installer determines what hardware is available and activates the appropriate module.  Each of those modules, depending on which is loaded, is updated automatically.  There is entirely no reason to add a PPA.  None.  AMD provides the open source amdgpu module to the kernel developers and the radeon module is maintained by the open source community.

There is generally nothing more to do.  However, in your case something was amiss.  But, since you have tried a couple of things your OS may be out of whack.

In any case, please post the results of the following commands.  The one that returns information will indicate which module is loaded.  I suspect is should be amdgpu.

```
lsmod | grep radeon
```

```
lsmod | grep amdgpu
```

---

### Post by hiker-guy on 2020-12-05
Thanks for the explanation QIII

I also thought my OS could just be out of whack but I'm on a fresh install of 20.04.1 now and the problem still persists.

The Radeon command does not return anything but this command:

```
lsmod | grep amdgpu
```

returns this:

```
amdgpu               4579328  0
amd_iommu_v2           20480  1 amdgpu
gpu_sched              32768  1 amdgpu
ttm                   106496  1 amdgpu
drm_kms_helper        184320  1 amdgpu
i2c_algo_bit           16384  1 amdgpu
drm                   491520  4 gpu_sched,drm_kms_helper,amdgpu,ttm

```

Also this command:

```
lspci -k | grep -EA3 'VGA|3D|Display'
```

returns this:

```
06:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Renoir (rev d1)
    Subsystem: Lenovo Renoir
    Kernel modules: amdgpu
06:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 1637

```

So it looks like I have amdgpu loaded but settings still displays 'Unknown Display' and I can't adjust the resolution. Do I need to enable the radeon module? As I have radeon graphics. How do I go about doing this?

---

### Post by QIII on 2020-12-05
No, you do not need to enable the radeon module.  You likely wouldn't be able to to begin with and if you were able to you would surely cause problems.  The installer properly activated the amdgpu module.

One must differentiate between "Radeon Graphics", which is AMD's branding, and radeon as in the open-source driver.  AMD has continued the "Radeon" branding even after having finally been successful in shaking the ATI association after purchasing ATI in 2006.

amdgpu is their driver for their new generation of GPUs.

That said:  AMD has to release the amdgpu code to the kernel developers for them to add it to the kernel.  As new models of GPUs come out, that code may change to work with the newer hardware.  For a time, the very newest hardware may only be supported by the very newest kernel.  We hope that in general some of that will get back-ported to older, but still supported, kernel versions.

I'll have to do a bit of research about your hardware.

---

### Post by QIII on 2020-12-05
It seems that Phoronix is pleased with the performance of the Renoir family [using Kernel 5.10]("https://www.phoronix.com/scan.php?page=news_item&px=AMD-Renoir-Linux-5.10").  Apparently 5.8 also works.  The earliest kernel version I have found so far that is said to work with Renoir is 5.5.

---

### Post by hiker-guy on 2020-12-05
Thanks for looking into it QIII

I've done a fresh install from an 20.10 ISO. This command:
```
uname -r
```

Returns this:
```
5.8.0-31-generic
```

So I have a 5.8 kernel but the 'unknown display' problem still persists.

This command:

```
sudo lshw -c video
```

Returns this:

```
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: Renoir
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:06:00.0
       version: d1
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix vga_controller bus_master cap_list
       configuration: latency=0
       resources: iomemory:40-3f iomemory:40-3f memory:460000000-46fffffff memory:470000000-4701fffff ioport:1000(size=256) memory:fd300000-fd37ffff


```

And now neither of these commands return anything:

```
lsmod | grep amdgpu
```
```
lsmod | grep radeon
```

Initially when I tried installing from a USB I was presented with this error:

```
AMD-Vi: Unable to read/write to IOMMU perf counter
```

I got round this by booting with safe graphics and then installing as normal. I have also installed the updates the OS recommended after install.

---

### Post by fatboyslim2 on 2021-03-09
Please find detailed how-to here:
[https://askubuntu.com/questions/1297325/new-radeon-graphics-with-ubuntu/1320189](https://askubuntu.com/questions/1297325/new-radeon-graphics-with-ubuntu/1320189)

---

