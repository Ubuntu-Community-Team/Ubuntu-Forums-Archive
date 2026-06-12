---
title: "Index out of range?"
date: 2024-02-04
forum: General Help
---

### Post by overlxrdyt on 2024-02-04
Hello everyone!
 
I hope you're doing well. 
I come to request your help because I encounter a problem that I am unable to solve. After an update of Ubuntu (installation of packets before turning off the computer), i'm unable to boot...

 I get the following message at startup:
```


[I][ 11.166036]
==
[ 11.166875] UBSAN: array-index-out-of-bounds in /build/linux-hwe-6.5-BV4m5T/1
inux-hwe-6.5-6.5.0/drivers/message/fusion/mptsas.c:2446:22
11.168073] index 1 is out of range for type 'MPI_SAS_IO_UNITO_PHY_DATA [1] 11.169109]
[
&#1057;
11.169939] ==
===
===
[ 11.170768] UBSAN: array-index-out-of-bounds in /build/linux-hwe-6.5-BV4m5T/1
inux-hwe-6.5-6.5.0/drivers/message/fusion/mptsas.c:2448:22
[
[
[
=
[
11.171963] index 1 is out of range for type 'MPI_SAS_IO_UNITO_PHY_DATA [1] ' 11.172939]
11.173769]
===
11.174597]  UBSAN: array-index-out-of-bounds in /build/linux-hwe-6.5-BV4m5T/1 [  11.175784] index 1 is out of range for type 'MPI_SAS_IO_UNITO PHY_DATA  [1] ' 11.176759]
inux-hwe-6.5-6.5.0/drivers/message/fusion/mptsas.c:2451:7
[
[
=
[
==
11.215817]
====
inux-hwe-6.5-6.5.0/drivers/message/fusion/mptsas.c:2443:46
[
11.255140]  UBSAN: array-index-out-of-bounds in /build/linux-hwe-6.5-BV4m5T/1  11.293171] index 2 is out of range for type 'MPI_SAS_IO_UNITO_PHY_DATA  [1] ' 11.312455]
====
/dev/sdc3: clean, 596336/15597568 files, 24774318/62382848 blocks

```

[/I]I tried a DPKG in Rescue mode, Ubuntu has downloaded some packets (about 250MB) and erase some obsolete ones, but that hasn't changed anything, I still have this message when I want to boot.

 However, if I go through the rescue mode and then I ask for a normal start, I able to access Ubuntu, but with a display in 1024 x 768 and only one of my 2 screens gives a signal.  So I thought it was the GC but I changed my Titan X for an RX 560 and even problem. I installed another graphic pilot and the problem persists...

I also switch with an other SSD with Debian to see if my hardware was faulty and run some tests, but nothing wrong.

If anyone has an idea or a solution, i can give as information as you want

Just in case, this is my (weird) configuration:
```

- Hp XW 8600
- 2 x Xeon x5460
- 32 go RAM DDR2 ECC
- Nvidia Titan X 
- 2 x 256go SSD
- 1x HDD 250 go HDD
- 1x NVME 128go SSD on NVME PCIe Adapter

```

---

### Post by dragonfly41 on 2024-02-04
Need more context. More clues. Nearest I could find from your dump. Might be a red herring.

[https://forums.developer.nvidia.com/t/ubsan-array-index-out-of-bounds-complaints-in-newer-kernels/271705](https://forums.developer.nvidia.com/t/ubsan-array-index-out-of-bounds-complaints-in-newer-kernels/271705)

---

### Post by MAFoElffen on 2024-02-05
From a comment in the link dragonfly41 provided: [https://forums.developer.nvidia.com/t/ubsan-array-index-out-of-bounds-complaints-in-newer-kernels/271705/6](https://forums.developer.nvidia.com/t/ubsan-array-index-out-of-bounds-complaints-in-newer-kernels/271705/6)
> 
I should note that this warning is harmless. It&#8217;s due to the wrong size being declared on some arrays in UVM. You can see it in the code here: [https://github.com/NVIDIA/open-gpu-kernel-modules/blob/main/kernel-open/nvidia-uvm/uvm_pmm_gpu.c#L224](https://github.com/NVIDIA/open-gpu-kernel-modules/blob/main/kernel-open/nvidia-uvm/uvm_pmm_gpu.c#L224) 105

These are C &#8220;flexible array members&#8221; and should just be declared with no size.

I thought about kernel boot parameters
> 
The kernel parses parameters from the kernel command line up to &#8220;&#8211;&#8221;; if it doesn&#8217;t recognize a parameter and it doesn&#8217;t contain a &#8216;.&#8217;, the parameter gets passed to init: parameters with &#8216;=&#8217; go into init&#8217;s environment, others are passed as command line arguments to init. Everything after &#8220;&#8211;&#8221; is passed as an argument to init.

 Module parameters can be specified in two ways: via the kernel command line with a module name prefix, or via modprobe, e.g.:

Often we'll use a boot parameter to reset a kernel config option...


There was a compile time option to turn off USAN checking (announced on the kernel lists), that will skip the warnings and turn the check off. There is also an option to leave it unconfigured or configured (To enable UBSAN configure kernel with: CONFIG_UBSAN=y). I believe in our kernels now, the option is on by default, other wise we wouldn't be getting these warnings. When that feature was announced, in the kernel lists, there was mention of an unknown undocumented boot parameter called ubsan_handle. That, in itself, throws an error message in journalctl, so I play with variations until I found some things that do notthrow errors, and seem to be accepted as a boot parameter...

What happens if you add these boot parameters
```

GRUB_CMDLINE_LINUX_DEFAULT="--- splash ubsan.handle=n config.ubsan=n"

```

---

### Post by Tadaen_Sylvermane on 2024-02-05
I haven't bothered tracking this one myself but I've seen it on Jammy with HWE and the current Elementary OS 7.1. In my case it sits there a minute then loads up anyway. As it hasn't caused me an issue I haven't felt the need to dig at it.
A quick search on the source file isolates the problem here. All 4 lines in the output above are in this section. But I have no idea where the struct is coming from nor am I remotely qualified.

```
    for (i = 0; i < port_info->num_phys; i++) {
        mptsas_print_phy_data(ioc, &buffer->PhyData[i]);
        port_info->phy_info[i].phy_id = i;
        port_info->phy_info[i].port_id =
            buffer->PhyData[i].Port;
        port_info->phy_info[i].negotiated_link_rate =
            buffer->PhyData[i].NegotiatedLinkRate;
        port_info->phy_info[i].portinfo = port_info;
        port_info->phy_info[i].handle =
            le16_to_cpu(buffer->PhyData[i].ControllerDevHandle);
    }
```

---

