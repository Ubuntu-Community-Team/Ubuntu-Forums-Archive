---
title: "internet issue"
date: 2015-12-07
forum: General Help
---

### Post by grerlic on 2015-12-07
Hello all,

i just install ubuntu in my pc that has all ready windows 10 x64, the installation was made in second HDD. 
From the begin i had problem with the internet and after installation still didnt manage to connect.
Also how can i make when the pc start to choose directly what os to load,  now i need to change boot priority on the hdd to load ubuntu.

YEP im new in ubuntu :p 

My best regards

---

### Post by grerlic on 2015-12-08
Any one can help ?

---

### Post by Ricardo_Velasco on 2015-12-08
Greeting:

I 'll try to help you .

I've seen some problems When installing GRUB Ubuntu and Windows 10 ..

You have the Possibility of reinstall the operating system .

But another question ?? .. Is on another disk apart the Ubuntu operating system ?

Or this on the same hard disk Windows 10 ?

---

### Post by grerlic on 2015-12-08
Hello Thank you in advance 

yes i can reinstall both os i just format the pc 

and yes each os has its own hdd 

windows has ssd 500gb 
ubuntu has hdd 80 gb

---

### Post by Ricardo_Velasco on 2015-12-08
Greeting:

Okay , please tell me make Ubuntu driver and the Internet adapter you are using.

I need to know more details please to help or try to help your problem .

Run on your terminal :

> lspci

lsusb

Please give me the best possible detail to help :)

---

### Post by grerlic on 2015-12-09
hello here some info 

```
lukas@lukas-g1-assassine:~$ sudo lspci
 
sudo: unable to resolve host lukas-g1-assassine
[sudo] password for lukas:
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:02.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:10.0 PIC: Intel Corporation 7500/5520/5500/X58 Physical and Link Layer Registers Port 0 (rev 13)
00:10.1 PIC: Intel Corporation 7500/5520/5500/X58 Routing and Protocol Layer Registers Port 0 (rev 13)
00:11.0 PIC: Intel Corporation 7500/5520/5500 Physical and Link Layer Registers Port 1 (rev 13)
00:11.1 PIC: Intel Corporation 7500/5520/5500 Routing & Protocol Layer Register Port 1 (rev 13)
00:13.0 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller (rev 13)
00:14.0 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:15.0 PIC: Intel Corporation 7500/5520/5500/X58 Trusted Execution Technology Registers (rev 13)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 IDE interface: Marvell Technology Group Ltd. Device 918a (rev 10)
02:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
03:00.0 VGA compatible controller: NVIDIA Corporation GK104 [GeForce GTX 680] (rev a1)
03:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)
05:00.0 Audio device: Creative Labs EMU20k2 [X-Fi Titanium Series] (rev 03)
06:00.0 Power PC: Freescale Semiconductor Inc MPC8308 (rev 10)
3f:00.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers (rev 05)
3f:00.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder (rev 05)
3f:02.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 0 (rev 05)
3f:02.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 (rev 05)
3f:03.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller (rev 05)
3f:03.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder (rev 05)
3f:03.4 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers (rev 05)
3f:04.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers (rev 05)
3f:04.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers (rev 05)
3f:04.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers (rev 05)
3f:04.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers (rev 05)
3f:05.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers (rev 05)
3f:05.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers (rev 05)
3f:05.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers (rev 05)
3f:05.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers (rev 05)
3f:06.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers (rev 05)
3f:06.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers (rev 05)
3f:06.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers (rev 05)
3f:06.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers (rev 05)
 
lukas@lukas-g1-assassine:~$ sudo lsusb
 
sudo: unable to resolve host lukas-g1-assassine
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 2109:3431 VIA Labs, Inc. Hub
Bus 003 Device 006: ID 0951:1666 Kingston Technology DataTraveler G4
Bus 003 Device 004: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 003 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 003: ID 046d:c07d Logitech, Inc.
Bus 007 Device 002: ID 046d:c22d Logitech, Inc. G510 Gaming Keyboard
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 2109:0810 VIA Labs, Inc. VL81x Hub
Bus 002 Device 004: ID 0bc2:50a5 Seagate RSS LLC FreeAgent GoFlex Desk USB 3.0
Bus 002 Device 002: ID 2109:0810 VIA Labs, Inc. VL81x Hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
lukas@lukas-g1-assassine:~$ sudo ifconfig
sudo: unable to resolve host lukas-g1-assassine
lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3369 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:253659 (253.6 KB)  TX bytes:253659 (253.6 KB)
 
lukas@lukas-g1-assassine:~$ sudo dhclient eth0
sudo: unable to resolve host lukas-g1-assassine
Cannot find device "eth0"
 
lukas@lukas-g1-assassine:~$ sudo dhclient eth1
sudo: unable to resolve host lukas-g1-assassine
Cannot find device "eth1"
 
lukas@lukas-g1-assassine:~$ sudo dhclient eth2
sudo: unable to resolve host lukas-g1-assassine
Cannot find device "eth2"
 
lukas@lukas-g1-assassine:~$ sudo dhclient eth3
sudo: unable to resolve host lukas-g1-assassine
Cannot find device "eth3"
 
lukas@lukas-g1-assassine:~$ sudo dhclient eth4
sudo: unable to resolve host lukas-g1-assassine
Cannot find device "eth4"
 
 
etc/network/interfaces  has this
 
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

---

### Post by Ricardo_Velasco on 2015-12-09
Greetings:

But my question was not answered ?

Type of connection you use to connect to the Internet?

Wired or wireless ?

Because as I see on the list it does not appear that sent me neither.

Please , if you can send me the brand of the network device to which you are connecting

---

### Post by grerlic on 2015-12-11
the connection is Wired and the modem i use is CELLPIPE  7130 RG

---

### Post by cariboo on 2015-12-11
> **grerlic said:**
> the connection is Wired and the modem i use is CELLPIPE  7130 RG

Could you please post the output of:

```
sudo lshw -C network
```

---

### Post by grerlic on 2015-12-11
if i add 
```
sudo lshw -C network
``` 

i dont get anything exept that it change very fast 2 or 3 words and the only word that i can see is USB 
but if i add 

```
sudo lshw -D network
```

i get 

```
lukas@lukas-g1-assassine:~$ sudo lshw -D network
 
sudo: unable to resolve host lukas-g1-assassine
Hardware Lister (lshw) - B.02.17
usage: lshw [-format] [-options ...]
       lshw -version
 
            -version        print program version (B.02.17)
 
format can be
            -html           output hardware tree as HTML
            -xml            output hardware tree as XML
            -short          output hardware paths
            -businfo        output bus information
 
options can be
            -class CLASS    only show a certain class of hardware
            -C CLASS        same as '-class CLASS'
            -c CLASS        same as '-class CLASS'
            -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
            -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
            -quiet          don't display status
            -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
            -numeric        output numeric IDs (for PCI, USB, etc.)

```

and if i add 

```
lshw  without sudo
```

i get 

```
WARNING: you should run this program as super-user.
lukas-g1-assassine       
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 5965MiB
     *-cpu
          product: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2261MHz
          capacity: 2661MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
     *-pci:0
          description: Host bridge
          product: 5520/5500/X58 I/O Hub to ESI Port
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 13
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 5520/5500/X58 I/O Hub PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:c000(size=4096) memory:fbc00000-fbcfffff
           *-ide UNCLAIMED
                description: IDE interface
                product: Marvell Technology Group Ltd.
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: ide cap_list
                configuration: latency=0
                resources: ioport:cf00(size=8) ioport:ce00(size=4) ioport:cd00(size=8) ioport:cc00(size=4) ioport:cb00(size=16) memory:fbcff000-fbcff1ff memory:fbc00000-fbc0ffff
        *-pci:1
             description: PCI bridge
             product: 5520/5500/X58 I/O Hub PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:fbb00000-fbbfffff
           *-usb
                description: USB controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:16 memory:fbbfe000-fbbfffff
        *-pci:2
             description: PCI bridge
             product: 5520/5500/X58 I/O Hub PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:d000(size=4096) memory:f6000000-f7ffffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: GK104 [GeForce GTX 680]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:35 memory:f6000000-f6ffffff memory:e0000000-e7ffffff memory:ee000000-efffffff ioport:df00(size=128) memory:f7000000-f707ffff
           *-multimedia
                description: Audio device
                product: GK104 HDMI Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:f7ffc000-f7ffffff
        *-generic:0 UNCLAIMED
             description: PIC
             product: 7500/5520/5500/X58 Physical and Link Layer Registers Port 0
             vendor: Intel Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: 8259 cap_list
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: PIC
             product: 7500/5520/5500/X58 Routing and Protocol Layer Registers Port 0
             vendor: Intel Corporation
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: 8259
             configuration: latency=0
        *-generic:2 UNCLAIMED
             description: PIC
             product: 7500/5520/5500 Physical and Link Layer Registers Port 1
             vendor: Intel Corporation
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: 8259 cap_list
             configuration: latency=0
        *-generic:3 UNCLAIMED
             description: PIC
             product: 7500/5520/5500 Routing & Protocol Layer Register Port 1
             vendor: Intel Corporation
             physical id: 11.1
             bus info: pci@0000:00:11.1
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: 8259
             configuration: latency=0
        *-generic:4 UNCLAIMED
             description: PIC
             product: 7500/5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: io_x_-apic bus_master cap_list
             configuration: latency=0
             resources: memory:fbfff000-fbffffff
        *-generic:5
             description: PIC
             product: 7500/5520/5500/X58 I/O Hub System Management Registers
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: 8259 cap_list
             configuration: driver=i7core_edac latency=0
             resources: irq:0
        *-generic:6 UNCLAIMED
             description: PIC
             product: 7500/5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers
             vendor: Intel Corporation
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: 8259 cap_list
             configuration: latency=0
        *-generic:7 UNCLAIMED
             description: PIC
             product: 7500/5520/5500/X58 I/O Hub Control Status and RAS Registers
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: 8259 cap_list
             configuration: latency=0
        *-generic:8 UNCLAIMED
             description: PIC
             product: 7500/5520/5500/X58 Trusted Execution Technology Registers
             vendor: Intel Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: io_x_-apic
             configuration: latency=0
        *-usb:0
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff00(size=32)
        *-usb:1
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:fe00(size=32)
        *-usb:2
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:fd00(size=32)
        *-usb:3
             description: USB controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:fbffe000-fbffe3ff
        *-pci:3
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:1000(size=4096) memory:f4000000-f41fffff ioport:f4200000(size=2097152)
        *-pci:4
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:2000(size=4096) memory:f8000000-f9ffffff ioport:f4400000(size=2097152)
           *-multimedia
                description: Audio device
                product: EMU20k2 [X-Fi Titanium Series]
                vendor: Creative Labs
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=snd_ctxfi latency=0
                resources: irq:17 memory:f9ff0000-f9ffffff memory:f9c00000-f9dfffff memory:f8000000-f8ffffff
        *-pci:5
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:3000(size=4096) memory:fbd00000-fbefffff ioport:fa000000(size=16777216)
           *-processor UNCLAIMED
                description: Power PC
                product: MPC8308
                vendor: Freescale Semiconductor Inc
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:fbd00000-fbdfffff memory:fbee0000-fbeeffff memory:fa000000-faffffff memory:fbefc000-fbefffff
        *-usb:4
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:fc00(size=32)
        *-usb:5
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:fb00(size=32)
        *-usb:6
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:fa00(size=32)
        *-usb:7
             description: USB controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:fbffd000-fbffd3ff
        *-pci:6
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode cap_list
        *-isa
             description: ISA bridge
             product: 82801JIR (ICH10R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f900(size=8) ioport:f800(size=4) ioport:f700(size=8) ioport:f600(size=4) ioport:f500(size=16) ioport:f400(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801JI (ICH10 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fbffc000-fbffc0ff ioport:500(size=32)
        *-ide:1
             description: IDE interface
             product: 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f200(size=8) ioport:f100(size=4) ioport:f000(size=8) ioport:ef00(size=4) ioport:ee00(size=16) ioport:ed00(size=16)
     *-pci:1
          description: Host bridge
          product: Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:3f:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Xeon 5500/Core i7 QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:3f:00.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Xeon 5500/Core i7 QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:3f:02.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Xeon 5500/Core i7 QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:3f:02.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:3f:03.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:3f:03.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Test Registers
          vendor: Intel Corporation
          physical id: 107
          bus info: pci@0000:3f:03.4
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers
          vendor: Intel Corporation
          physical id: 108
          bus info: pci@0000:3f:04.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers
          vendor: Intel Corporation
          physical id: 109
          bus info: pci@0000:3f:04.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers
          vendor: Intel Corporation
          physical id: 10a
          bus info: pci@0000:3f:04.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:11
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10b
          bus info: pci@0000:3f:04.3
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:12
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers
          vendor: Intel Corporation
          physical id: 10c
          bus info: pci@0000:3f:05.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:13
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers
          vendor: Intel Corporation
          physical id: 10d
          bus info: pci@0000:3f:05.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:14
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers
          vendor: Intel Corporation
          physical id: 10e
          bus info: pci@0000:3f:05.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:15
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10f
          bus info: pci@0000:3f:05.3
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:16
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers
          vendor: Intel Corporation
          physical id: 110
          bus info: pci@0000:3f:06.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:17
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers
          vendor: Intel Corporation
          physical id: 111
          bus info: pci@0000:3f:06.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:18
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers
          vendor: Intel Corporation
          physical id: 112
          bus info: pci@0000:3f:06.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:19
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 113
          bus info: pci@0000:3f:06.3
          version: 05
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: BD-RE  GGW-H20L
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: YL05
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

---

