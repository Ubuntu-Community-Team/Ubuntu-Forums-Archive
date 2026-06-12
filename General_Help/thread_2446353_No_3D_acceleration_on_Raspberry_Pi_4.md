---
title: "No 3D acceleration on Raspberry Pi 4"
date: 2020-06-29
forum: General Help
---

### Post by chris-hancox on 2020-06-29
Hi there,

I recently installed Ubuntu 20.04 on the Raspberry Pi 4. It is the official server release and I then downloaded Ubuntu MATE to serve as a desktop. However, no matter what I do, I cannot enable GPU Acceleration. I posted on the Raspbian forums, and they said it is this way by design on Ubuntu? But that makes no sense to gimp GPU acceleration just because it is a server release?

lsmod | grep v3d shows:
v3d 73728 0
gpu_sched 45056 1 v3d
drm 569344 6 gpu_sched,drm_kms_helper,v3d,vc4

Sorry, I had to type by hand, rather than copy and paste.

Glxinfo always shows llvmpipe no matter what I do.

I have various things installed on this: 0 A.D, OpenRA, OpenRCT2, OpenMW, etc, and surprisingly all run, but obviously poorly without acceleration. Does anyone know how to get to the bottom of this?

---

### Post by ActionParsnip on 2020-06-29
What is the output of:
```

sudo lshw -C display

```
Thanks

---

### Post by chris-hancox on 2020-06-29
there is no output with that command.

```
ubuntu@ubuntu:~$ sudo lshw 
ubuntu                      
    description: Computer
    product: Raspberry Pi 4 Model B Rev 1.1
    serial: 10000000cb4fa6f5
    width: 64 bits
    capabilities: smp cp15_barrier setend swp tagged_addr_disabled
  *-core
       description: Motherboard
       physical id: 0
     *-cpu:0
          description: CPU
          product: cpu
          physical id: 1
          bus info: cpu@0
          size: 2100MHz
          capacity: 2100MHz
          capabilities: fp asimd evtstrm crc32 cpuid cpufreq
     *-cpu:1
          description: CPU
          product: cpu
          physical id: 2
          bus info: cpu@1
          size: 2100MHz
          capacity: 2100MHz
          capabilities: fp asimd evtstrm crc32 cpuid cpufreq
     *-cpu:2
          description: CPU
          product: cpu
          physical id: 3
          bus info: cpu@2
          size: 2100MHz
          capacity: 2100MHz
          capabilities: fp asimd evtstrm crc32 cpuid cpufreq
     *-cpu:3
          description: CPU
          product: cpu
          physical id: 4
          bus info: cpu@3
          size: 2100MHz
          capacity: 2100MHz
          capabilities: fp asimd evtstrm crc32 cpuid cpufreq
     *-memory
          description: System memory
          physical id: 5
          size: 3485MiB
     *-pci
          description: PCI bridge
          product: Broadcom Inc. and subsidiaries
          vendor: Broadcom Inc. and subsidiaries
          physical id: 0
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:44 memory:600000000-6000fffff
        *-usb
             description: USB controller
             product: VL805 USB 3.0 Host Controller
             vendor: VIA Technologies, Inc.
             physical id: 0
             bus info: pci@0000:01:00.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:45 memory:600000000-600000fff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.4.0-1013-raspi xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 5.04
                capabilities: usb-2.00
                configuration: driver=hub slots=1 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: VIA Labs, Inc.
                   physical id: 1
                   bus info: usb@1:1
                   version: 4.21
                   capabilities: usb-2.10
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb
                      description: Keyboard
                      product: 2.4G Composite Devic
                      physical id: 4
                      bus info: usb@1:1.4
                      version: 2.00
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.4.0-1013-raspi xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.04
                capabilities: usb-3.00
                configuration: driver=hub slots=4 speed=5000Mbit/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: dc:a6:32:66:03:8e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmfmac driverversion=7.45.154 firmware=01-4fbe0b04 ip=192.168.1.2 multicast=yes wireless=IEEE 802.11
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: eth0
       serial: dc:a6:32:66:03:8d
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=bcmgenet driverversion=v2.0 link=no multicast=yes port=MII


```

---

### Post by intel-user on 2020-06-29
I to have tried everything I know with dtoverlay changes etc and also do not get any 3D acceleration on a Pi 4 8Gb model.

I think the issue may be related to the following bug report I have located :-

[https://bugs.launchpad.net/ubuntu/+source/linux-raspi/+bug/1880125](https://bugs.launchpad.net/ubuntu/+source/linux-raspi/+bug/1880125)

which is confirmed and outstanding with the last entry on 25th June 2020.

I think this is a major issue that should be fixed ASAP before many Raspberry users abandon Ubuntu altogether as a Desktop alternative option.

---

### Post by chris-hancox on 2020-06-29
That bug is interesting and a shame, I am aware that Canonical only support the Server side but this is obviously a severe issue.

I would like to know if there are any more terminal commands I can do that could give some insight to the problem to non-Pi 4 owners?

---

### Post by intel-user on 2020-06-30
Not sure if these messages from the kernel Linux ubuntu 5.4.0-1012-raspi #12-Ubuntu SMP Wed May 27 04:08:35 UTC 2020 aarch64 aarch64 aarch64 GNU/Linux
may indicate that the V3D driver is not starting up correctly and generating the required /dev/ entries.
The first line appears to indicate that the probe has not received the expected number of output ports which then appears to remove the /dev entries.

[    6.353424] bcm2835-isp bcm2835-isp: bcm2835_isp_probe: ril.isp returned 1 i/p (1 expected), 2 o/p (3 expected) ports
[    6.364171] bcm2835-isp bcm2835-isp: Unregister from media controller
[    6.364181] (efault): Unregistering node (null)[0] device node /dev/video0
[    6.364184] (efault): Unregistering node (null)[0] device node /dev/video0
[    6.364187] (efault): Unregistering node (null)[0] device node /dev/video0
[    6.364191] (efault): Unregistering node (null)[0] device node /dev/video0

---

### Post by chris-hancox on 2020-06-30
Can we work out why the V3D driver isn't recieving the correct number of ports?

---

### Post by intel-user on 2020-07-01
I have given up for the present with this and returned to the 64 bit Pi OS beta which runs the V3D driver correctly under the 5.4.0 kernel.
WebGL 2 samples get over 20 frames a second compared with 5 in Ubuntu and videos play with up to a 50% saving on CPU resources.
Will monitor the situation and can try again should progress be made on this issue.

---

### Post by chris-hancox on 2020-07-06
As of today, I have received 1014 version kernel, and 3D acceleration is fixed!

---

### Post by intel-user on 2020-07-06
Wow that's good news .... I need to test this out .... thanks for the heads up.

---

### Post by intel-user on 2020-07-06
Yes .... got the 1014 kernel update and now the V3D 4.2 pi driver is showing as in use, so fixed.
Clearly some change to the kernel has been included/picked up as a patch and has fixed the issue.

---

### Post by dafna3 on 2020-09-23
> **intel-user said:**
> Not sure if these messages from the kernel Linux ubuntu 5.4.0-1012-raspi #12-Ubuntu SMP Wed May 27 04:08:35 UTC 2020 aarch64 aarch64 aarch64 GNU/Linux
may indicate that the V3D driver is not starting up correctly and generating the required /dev/ entries.
The first line appears to indicate that the probe has not received the expected number of output ports which then appears to remove the /dev entries.

[    6.353424] bcm2835-isp bcm2835-isp: bcm2835_isp_probe: ril.isp returned 1 i/p (1 expected), 2 o/p (3 expected) ports
[    6.364171] bcm2835-isp bcm2835-isp: Unregister from media controller
[    6.364181] (efault): Unregistering node (null)[0] device node /dev/video0
[    6.364184] (efault): Unregistering node (null)[0] device node /dev/video0
[    6.364187] (efault): Unregistering node (null)[0] device node /dev/video0
[    6.364191] (efault): Unregistering node (null)[0] device node /dev/video0

Hi, I got the exact same error with rpi3  Model B+ on both kernle version 5.4 and 5.8
were you able to fix it ?

---

