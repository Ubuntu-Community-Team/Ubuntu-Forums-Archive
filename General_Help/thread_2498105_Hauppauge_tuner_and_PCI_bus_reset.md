---
title: "Hauppauge tuner and PCI bus reset"
date: 2024-05-30
forum: General Help
---

### Post by vidtek on 2024-05-30
I recently upgraded to Noble 24 from Jammy 22 and the Hauppauge quad PCI tuner drops out after about 1/2 hour or so.

I can bring it back online with this script I cobbled together from various sources on PCI issues, but it isn't a lot of good with a tv tuner set for automatic recording!

```
echo "1" > /sys/bus/pci/devices/0000:07:00.0/remove
    sleep 2
   	echo "1" > /sys/bus/pci/rescan
    	echo "2" > /sys/bus/pci/devices/0000:08:00.0/remove
    sleep 2
    	echo "2" > /sys/bus/pci/rescan
```  

The system worked well for a couple of years on Jammy.

This is the result of a PCI scan:-
```
tony@linuxmint:~$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 05)
00:01.0 PCI bridge: Intel Corporation 6th-10th Gen Core Processor PCIe Controller (x16) (rev 05)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x8) (rev 05)
00:14.0 USB controller: Intel Corporation 200 Series/Z370 Chipset Family USB 3.0 xHCI Controller
00:16.0 Communication controller: Intel Corporation 200 Series PCH CSME HECI #1
00:17.0 SATA controller: Intel Corporation 200 Series PCH SATA controller [AHCI mode]
00:1b.0 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #17 (rev f0)
00:1b.4 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #21 (rev f0)
00:1c.0 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #1 (rev f0)
00:1c.4 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #5 (rev f0)
00:1c.6 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #7 (rev f0)
00:1d.0 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #9 (rev f0)
00:1f.0 ISA bridge: Intel Corporation 200 Series PCH LPC Controller (Z270)
00:1f.2 Memory controller: Intel Corporation 200 Series/Z370 Chipset Family Power Management Controller
00:1f.3 Audio device: Intel Corporation 200 Series PCH HD Audio
00:1f.4 SMBus: Intel Corporation 200 Series/Z370 Chipset Family SMBus Controller
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (2) I219-V
01:00.0 VGA compatible controller: NVIDIA Corporation TU116 [GeForce GTX 1660] (rev a1)
01:00.1 Audio device: NVIDIA Corporation TU116 High Definition Audio Controller (rev a1)
01:00.2 USB controller: NVIDIA Corporation TU116 USB 3.1 Host Controller (rev a1)
01:00.3 Serial bus controller: NVIDIA Corporation TU116 USB Type-C UCSI Controller (rev a1)
02:00.0 Non-Volatile memory controller: SK hynix PC401 NVMe Solid State Drive 256GB
03:00.0 Non-Volatile memory controller: Micron/Crucial Technology P2 [Nick P2] / P3 / P3 Plus NVMe PCIe SSD (DRAM-less) (rev 01)
04:00.0 Non-Volatile memory controller: Phison Electronics Corporation E12 NVMe Controller (rev 01)
05:00.0 PCI bridge: Pericom Semiconductor PI7C9X2G304 EL/SL PCIe2 3-Port/4-Lane Packet Switch (rev 05)
06:01.0 PCI bridge: Pericom Semiconductor PI7C9X2G304 EL/SL PCIe2 3-Port/4-Lane Packet Switch (rev 05)
06:02.0 PCI bridge: Pericom Semiconductor PI7C9X2G304 EL/SL PCIe2 3-Port/4-Lane Packet Switch (rev 05)
07:00.0 Multimedia video controller: Conexant Systems, Inc. CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb (rev 04)
08:00.0 Multimedia video controller: Conexant Systems, Inc. CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb (rev 04)
09:00.0 USB controller: ASMedia Technology Inc. ASM2142/ASM3142 USB 3.1 Host Controller
0a:00.0 USB controller: ASMedia Technology Inc. ASM2142/ASM3142 USB 3.1 Host Controller
0b:00.0 Non-Volatile memory controller: Micron/Crucial Technology P2 [Nick P2] / P3 / P3 Plus NVMe PCIe SSD (DRAM-less) (rev 01)
tony@linuxmint:~$ 

```

Hardware: Asus  STRIX Z270E GAMING v: Rev 1.xx serial: 170706774500147 Mobo.
   Bios        UEFI: American Megatrends v: 1302 date: 03/15/2018 
CPU Intel I7, 16gb ram 
GPU Nvidia GTX1660 
Hauppauge Quad Win-tv model 01607  as here:[https://www.hauppauge.co.uk/site/products/data_quadhd.html]("https://www.hauppauge.co.uk/site/products/data_quadhd.html")

I know the system is getting a bit old, but it has worked well until Noble Nutter 24 (sorry can't remember the exact name of it)

Any suggestions very welcome.

Tony.

---

### Post by vidtek on 2024-06-22
In desperation I tried swapping the Hauppauge card for an older TBS quad tuner from my backup (even older) machine.

Interestingly, the TBS card behaves in exactly the same way as the Hauppauge card does, dropping out after about an hour or so.

Here are it's details:```
07:00.0 Multimedia controller: TBS Technologies DVB Tuner PCIe Card
        Subsystem: TBS Technologies (wrong ID) TBS6205 DVB-T2/T/C Quad TV Tuner PCIe Card
        Flags: bus master, fast devsel, latency 0, IRQ 179
        Memory at df200000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: [50] Power Management version 3
        Capabilities: [70] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [90] Express Endpoint, MSI 00
        Capabilities: [100] Device Serial Number 00-00-00-00-00-00-00-00
        Kernel driver in use: TBSECP3 driver
        Kernel modules: tbsecp3

```

I then re-installed an old Jammy 20.04 backup and it drops out on this version too.

I'm beginning to think it may be a hardware issue with my motherboard, although I did try a different PCIe slot for the cards and it still drops out.

I wonder if I insert acpi=off into the grub boot line maybe????

Help!  Tony

---

### Post by vidtek on 2024-06-23
Well it looks as though I may have stumbled upon a solution.   I edited the grub command line with this:```
net.ifnames=0 biosdevname=0 pci=noacpi
```

The pci=noacpi entry seems to have done the trick.   The first entry is just to keep the wired lan name as eth0 instead of some random system assigned string.

I managed to record a show in the middle of the night last night and it was successful.  I will need to do more testing, but previously it would always fail.

I'll mark this thread as solved.

Tony.

---

