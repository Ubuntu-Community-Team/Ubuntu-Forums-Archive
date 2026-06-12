---
title: "Ubuntu not running decently on recent hardware (intel NUC10i7FNB)"
date: 2022-02-12
forum: General Help
---

### Post by cactux on 2022-02-12
Hello,

Is it possible to make Ubuntu running decently on a Intel NUC mini-PC ? Model NUC10i7FNB.
This hardware is quite recent, has i7 processors, 32GB RAM, SSD, I though that Ubuntu would be really fast and responsive, but it is not.
My wife and kids complain a lot, especially in Firefox which from time to time is not responsive (restarting Firefox helps when it happens).
With such specs, I really thought I'd have a slick & fast & responsive Linux.

I did the basic install, no specific tweaks or configuration.

What would you recommend?

Here's the output of "lspci" and "hwinfo --short", tell me if you need more information.
```
$ lspci
00:00.0 Host bridge: Intel Corporation Device 9b51
00:02.0 VGA compatible controller: Intel Corporation Device 9bca (rev 04)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
00:12.0 Signal processing controller: Intel Corporation Comet Lake Thermal Subsytem
00:14.0 USB controller: Intel Corporation Device 02ed
00:14.2 RAM memory: Intel Corporation Device 02ef
00:14.3 Network controller: Intel Corporation Wireless-AC 9462
00:15.0 Serial bus controller [0c80]: Intel Corporation Serial IO I2C Host Controller
00:15.2 Serial bus controller [0c80]: Intel Corporation Device 02ea
00:16.0 Communication controller: Intel Corporation Comet Lake Management Engine Interface
00:17.0 SATA controller: Intel Corporation Comet Lake SATA AHCI Controller
00:1c.0 PCI bridge: Intel Corporation Device 02bc (rev f0)
00:1d.0 PCI bridge: Intel Corporation Device 02b0 (rev f0)
00:1d.5 PCI bridge: Intel Corporation Device 02b5 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Device 0284
00:1f.3 Audio device: Intel Corporation Device 02c8
00:1f.4 SMBus: Intel Corporation Device 02a3
00:1f.5 Serial bus controller [0c80]: Intel Corporation Comet Lake SPI (flash) Controller
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (10) I219-V
01:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
02:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
02:01.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
02:02.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
03:00.0 System peripheral: Intel Corporation JHL7540 Thunderbolt 3 NHI [Titan Ridge 2C 2018] (rev 06)
39:00.0 USB controller: Intel Corporation JHL7540 Thunderbolt 3 USB Controller [Titan Ridge 2C 2018] (rev 06)
3a:00.0 Non-Volatile memory controller: Kingston Technology Company, Inc. Device 500f (rev 03)
3b:00.0 SD Host controller: Genesys Logic, Inc Device 9755

```

```
cpu:                                                            
                       Intel(R) Core(TM) i7-10710U CPU @ 1.10GHz, 1600 MHz
                       Intel(R) Core(TM) i7-10710U CPU @ 1.10GHz, 1600 MHz
                       Intel(R) Core(TM) i7-10710U CPU @ 1.10GHz, 1600 MHz
                       Intel(R) Core(TM) i7-10710U CPU @ 1.10GHz, 1600 MHz
                       Intel(R) Core(TM) i7-10710U CPU @ 1.10GHz, 1600 MHz
                       Intel(R) Core(TM) i7-10710U CPU @ 1.10GHz, 1600 MHz
                       Intel(R) Core(TM) i7-10710U CPU @ 1.10GHz, 1600 MHz
                       Intel(R) Core(TM) i7-10710U CPU @ 1.10GHz, 1625 MHz
                       Intel(R) Core(TM) i7-10710U CPU @ 1.10GHz, 1600 MHz
                       Intel(R) Core(TM) i7-10710U CPU @ 1.10GHz, 1600 MHz
                       Intel(R) Core(TM) i7-10710U CPU @ 1.10GHz, 1057 MHz
                       Intel(R) Core(TM) i7-10710U CPU @ 1.10GHz, 1600 MHz
keyboard:
  /dev/input/event6    Dell Keyboard
mouse:
  /dev/input/mice      IBM ThinkPad 800dpi Optical Travel Mouse
  /dev/input/mice      IBM ThinkPad 800dpi Optical Travel Mouse
monitor:
                       Lenovo LEN D32q-20B
                       AOC Q3279WG5B
graphics card:
                       Intel VGA compatible controller
sound:
                       Intel Audio device
                       JMTek, LLC USB PnP Audio Device
storage:
                       Intel SATA controller
                       Kingston Technology Company Non-Volatile memory controller
network:
  wlp0s20f3            Intel WLAN controller
  eno1                 Intel Ethernet Connection (10) I219-V
network interface:
  wlp0s20f3            Ethernet network interface
  lo                   Loopback network interface
  eno1                 Ethernet network interface
disk:
  /dev/nvme0n1         Kingston Technology Company Disk
  /dev/sda             ST2000LM015-2E81
partition:
  /dev/nvme0n1p1       Partition
  /dev/nvme0n1p2       Partition
  /dev/nvme0n1p3       Partition
  /dev/sda1            Partition
usb controller:
                       Intel JHL7540 Thunderbolt 3 USB Controller [Titan Ridge 2C 2018]
                       Intel USB Controller
bios:
                       BIOS
bridge:
                       Intel PCI bridge
                       Intel ISA bridge
                       Intel JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018]
                       Intel JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018]
                       Intel Host bridge
                       Intel JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018]
                       Intel PCI bridge
                       Intel JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018]
                       Intel PCI bridge
hub:
                       Dell Keyboard Hub
                       Linux Foundation 2.0 root hub
                       Linux Foundation 3.0 root hub
                       Linux Foundation 2.0 root hub
                       Linux Foundation 3.0 root hub
memory:
                       Main Memory
bluetooth:
                       Intel Bluetooth Device
unknown:
                       FPU
                       DMA controller
                       PIC
                       Keyboard controller
                       Intel JHL7540 Thunderbolt 3 NHI [Titan Ridge 2C 2018]
                       Genesys Logic SD Host controller
                       Intel Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
                       Intel Communication controller
                       Intel Serial bus controller
                       Intel Serial bus controller
                       Intel Signal processing controller
                       Intel Serial bus controller
                       Intel RAM memory
                       Intel SMBus
  /dev/input/event9    Dell Keyboard
  /dev/input/event5    JMTek, LLC USB PnP Audio Device
                       Chrontel Billboard

```

---

### Post by TheFu on 2022-02-13
Actually, posting the output from 
**inxi -Fxxz **
is much more readable and provides the more important facts at the right detail level.  The Dell output is providing generic terms.
```
memory:
                       Main Memory
```
isn't exactly useful.

For desktop use, the GPU is what matters most, provided the correct drivers are used, then using an NVMe SSD, followed by having sufficient RAM and the CPU is usually the least important.

And it is important to no choose certain setup options and to size the swap correctly. In theory, your hardware should handle anything well, unless there is a thermal problem causing throttling.  I had a 1st-gen Core i7 miniPC that had poor cooling, so the CPUs all ran 30% slower so they wouldn't burn out. That box had a CAD nvidia GPU, so graphics stuff wasn't the slowdown. When I checked the logs, I could see all the thermal throttle messages.

If you want something that feels faster, avoid Gnome3 (though it should be fine on your system). Almost any other DE will feel faster because it doesn't have the hundreds of bloated things that Gnome3+ adds.

Oh, and using a fast DNS matters too. Lots of things on Linux hit the network to check stuff. A slow DNS (slow router, if that's where your DNS caching happens) has previously made any OS feel slow. Most people would want to use 1.1.1.1 and 1.0.0.1 DNS for speed and privacy.

IMHO.

I run my desktop inside a virtual machine with 1 vCPU and 4G of RAM. Feels snappy to me with a minimal interface.

I'm not sure if this matters, but I've read that thunderbolt is an issue for some people.

---

### Post by tea for one on 2022-02-13
I have an NUCi3BEH with a Kingston NVME drive and I added a parameter to Grub to improve occasional slow response.
Info here [https://www.tekbyte.net/fixing-nvme-ssd-problems-on-linux/](https://www.tekbyte.net/fixing-nvme-ssd-problems-on-linux/)

Sometimes, it is helpful to remove all peripheral devices and just start with a known reliable mouse and keyboard.

---

### Post by oldfred on 2022-02-13
Have you updated UEFI to latest firmware?
And updated SSD to latest firmware?

---

### Post by MAFoElffen on 2022-02-14
I went through your computers specs... Nice PC. It has a fast CPU (Turbo Mode of up to 4.7 GHz), very fast NVMe storage, Optane capable storage caching, support Memory up to 64GB at 2666 MHz, etc. Looking at it's spec's you probably have at least 16 GB of RAM.

Usually the number one upgrade that 'would' increase performance in a Desktop would be to add a high-end GPU, but your computer does not support that kind of upgrade. (PCIex4 slot) The existing APU (Intel UHD Graphics 620) is in about at the level of a low-end gaming graphics.

Your concentration should be a using a fast DNS (1.1.1.1 and 1.1.1.0), a caching DNS, networking devices that support throughput, etc.

---

### Post by HermanAB on 2022-02-15
If you want speed, then you should use almost anything except Ubuntu.  The fastest systems by a wide margin are Slackware and OpenBSD.  Those two will blow your socks off.  However, I could recommend Xubuntu for reasonable speed.

---

### Post by MAFoElffen on 2022-02-15
Well...

If you ran the UbuntuForums 'system-info' script (link in my signature line), you could gather the hardware, system, and configuration information and upload a sanitized copy for you to a pastebin. That would enable us to see (in detail) what we are recommending solutions for. 

We all have our opinions on what to run, and that might be biased on what we use. I made assumption on your computer spec's based on how it is sold... It shoul run Ubuntu very fast, based on those basic assumptions.

But from where you said it was slow, or lacking, it doesn't matter which flavor, nor distribution you run, for web browsing, besides the rendering of (which you have good graphics capabilities), the biggest bottleneck would be 'network related.'

---

### Post by cactux on 2022-02-16
First, thanks a lot for all these answers!

I'll try the network path first, especially the DNS recommendations as soon as I have time (difficult during the week).
Then all other ideas of course if needed :)

I chose Ubuntu because this PC is used by all the family (wife, kids, and me). I want it to be user friendly, a no-brainer to use. I've gone through Slack, Mandrake, Mandriva, Kubuntu to settle on Ubuntu since a few years but I can change again.

Here's the output from system-info:

```
Starting the Ubuntu Forums 'system-info' Report: 2022-02-16  08:23:16 CET (+0100)
	Part of the Ama-gi Project
	Version: 01.00-03, Script Date: 2022.02.09

---------------------------------------------------------------
Main Complaint: Slow Ubuntu
Problem Description:  Ubuntu is quite often slow, with these specs I thought it would be real fast
---------- General Computer Specifications:

  --- Computer/CPU Information from 'lshw -C cpu' --- 
*-Cpu
    Description: CPU
    Product: Intel(R) Core(TM) i7-10710U CPU @ 1.10GHz
    Vendor: Intel Corp.
    Physical id: 44
    Bus info: cpu@0
    Version: Intel(R) Core(TM) i7-10710U CPU @ 1.10GHz
    Serial: [REMOVED]
    Slot: U3E1
    Size: 3188MHz
    Capacity: 4700MHz
    Width: 64 bits
    Clock: 100MHz
    Capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 
        apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse 
        sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art 
        arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid 
        aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg 
        fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt 
        tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch 
        cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced 
        tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust sgx 
        bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt 
        intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp 
        hwp_notify hwp_act_window hwp_epp md_clear flush_l1d arch_capabilities 
        cpufreq
    Configuration: cores=6 enabledcores=6 threads=12

computer
    Description: Mini PC
    Product: NUC10i7FNH (BXNUC10i7FNH)
    Vendor: Intel(R) Client Systems
    Version: K61081-302
    Serial: [REMOVED]
    Width: 64 bits
    Capabilities: smbios-3.2.0 dmi-3.2.0 smp vsyscall32
    Configuration:
        boot=normal
        chassis=mini
        family=FN
        sku=BXNUC10i7FNH
        uuid=[REMOVED]

------------------ SMBIOS Information from '/sys/class/dmi/id/' 
Bios Vendor:         Intel Corp.
Bios Version:        FNCML357.0039.2020.0312.1734
Bios Release:        5.16
Board Vendor:        Intel Corporation
Board Name:          NUC10i7FNB
Board Version:       K61360-302
Board Serial:        GEFN00100456
Board Asset Tag:     Default string

Current boot mode:   UEFI Firmware mode
SecureBoot disabled


---------- Memory Information:
              total        used        free      shared  buff/cache   available
Mem:           31Gi       4.0Gi       247Mi       997Mi        26Gi        25Gi
Swap:         975Mi       762Mi       213Mi

---------- IP Address Information:
  --- IP Address Information from 'ip addr' --- 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
    inet6 [REMOVED]
    inet6 [REMOVED]
3: wlp0s20f3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
    inet6 [REMOVED]
    inet6 [REMOVED]
    inet6 [REMOVED]
    inet6 [REMOVED]
    inet6 [REMOVED]

  --- Internet Connection Status from 'ping [various addresses]' --- 
Connected to Internet with DNS

  --- Network Device Status Summary from 'ip addr' ---  
These Network Devices are up:
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
3: wlp0s20f3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000

  --- Hostname from 'hostname --fqdn' ---  
The 'Hostname' of the computer system is: pcbureau


---------- File system specs from 'df -h':
Filesystem                                   Type      Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu-root                    ext4      914G  199G  669G  23% /
/dev/sda1                                    ext4      1.8T  672G  1.1T  39% /media/sda1
/dev/nvme0n1p2                               ext4      705M  240M  415M  37% /boot
/dev/nvme0n1p1                               vfat      511M  5.3M  506M   2% /boot/efi
[REMOVED]:/volume1/[REMOVED]                  nfs       3.6T  2.4T  1.2T  67% /media/diskstation/[REMOVED]
[REMOVED]:/volume1/[REMOVED]                  nfs       3.6T  2.4T  1.2T  67% /media/diskstation/[REMOVED]
[REMOVED]:/volume2/[REMOVED]                  nfs       7.3T  4.5T  2.8T  62% /media/diskstation/[REMOVED]
[REMOVED]:/volume1/[REMOVED]                  nfs       3.6T  2.4T  1.2T  67% /media/diskstation/[REMOVED]
[REMOVED]:/volume1/[REMOVED]                  nfs       3.6T  2.4T  1.2T  67% /media/diskstation/[REMOVED]
[REMOVED]:/volume1/[REMOVED]                  nfs       3.6T  2.4T  1.2T  67% /media/diskstation/[REMOVED]
[REMOVED]:/volume1/[REMOVED]                  nfs       3.6T  2.4T  1.2T  67% /media/diskstation/[REMOVED]
[REMOVED]:/volume1/[REMOVED]                  nfs       3.6T  2.4T  1.2T  67% /media/diskstation/[REMOVED]

---------- Disk/Partition Information From 'fdisk':

Disk /dev/nvme0n1: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: KINGSTON SNVS1000G                      
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 02D5EDA1-9D13-4F94-80FB-B59A1228004E

Device           Start        End    Sectors   Size Type
/dev/nvme0n1p1    2048    1050623    1048576   512M EFI System
/dev/nvme0n1p2 1050624    2549759    1499136   732M Linux filesystem
/dev/nvme0n1p3 2549760 1953523711 1950973952 930.3G Linux filesystem

Disk /dev/sda: 1.84 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: ST2000LM015-2E81
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x91070ece

Device     Boot Start        End    Sectors  Size Id Type
/dev/sda1        2048 3907029167 3907027120  1.8T 83 Linux

Disk /dev/mapper/nvme0n1p3_crypt: 930.29 GiB, 998881886208 bytes, 1950941184 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/mapper/vgubuntu-root: 929.33 GiB, 997854281728 bytes, 1948934144 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/mapper/vgubuntu-swap_1: 976 MiB, 1023410176 bytes, 1998848 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


---------- Disk/Partition Information From 'lsblk':
NAME                    SIZE FSTYPE      LABEL MOUNTPOINT                    MODEL
sda                     1.8T                                                 ST2000LM015-2E8174
`-sda1                  1.8T ext4              /media/sda1                   
nvme0n1               931.5G                                                 KINGSTON SNVS1000G
|-nvme0n1p1             512M vfat              /boot/efi                     
|-nvme0n1p2             732M ext4              /boot                         
`-nvme0n1p3           930.3G crypto_LUKS                                     
  `-nvme0n1p3_crypt   930.3G LVM2_member                                     
    |-vgubuntu-root   929.3G ext4              /                             
    `-vgubuntu-swap_1   976M swap              [SWAP]                        
   ------- 'lsblk' information continued ...
NAME                  HOTPLUG PARTUUID                             UUID
sda                         0                                      
`-sda1                      0 91070ece-01                          838609c5-aab9-4972-baea-1b9552a0aa1e
nvme0n1                     0                                      
|-nvme0n1p1                 0 32ef4ba3-b69c-4704-9379-2c695b833b96 BFA8-CE4B
|-nvme0n1p2                 0 b9b3abdb-816a-4acd-8029-e0246c630da0 d6de405a-6fef-4efb-846d-acd5b6abda9c
`-nvme0n1p3                 0 8d9abf9d-ec7d-432f-aa5e-51c1bf722547 7b7cb6e8-fec7-475c-b76f-6806df845bc2
  `-nvme0n1p3_crypt         0                                      npFnFZ-PkSh-WFbH-wMH9-noDE-H25k-0usI1V
    |-vgubuntu-root         0                                      2b511608-e477-4a74-91b6-46c1b466e3dc
    `-vgubuntu-swap_1       0                                      6d6acd72-de80-4439-9648-8512f1d8cbd4

---------- Mount Details of '/etc/fstab':
/dev/mapper/vgubuntu-root /               ext4    errors=remount-ro 0       1
UUID=d6de405a-6fef-4efb-846d-acd5b6abda9c /boot           ext4    defaults        0       2
UUID=BFA8-CE4B  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/vgubuntu-swap_1 none            swap    sw              0       0

UUID=838609c5-aab9-4972-baea-1b9552a0aa1e /media/sda1     ext4    defaults        0       0


[REMOVED]:/volume2/[REMOVED] /media/diskstation/[REMOVED] nfs nouser,rsize=8192,wsize=8192,atime,auto,rw,dev,exec,suid 0 0
[REMOVED]:/volume1/[REMOVED] /media/diskstation/[REMOVED] nfs rw,hard,intr,nolock 0 0
[REMOVED]:/volume1/[REMOVED] /media/diskstation/[REMOVED] nfs nouser,rsize=8192,wsize=8192,atime,auto,rw,dev,exec,suid 0 0
[REMOVED]:/volume1/[REMOVED] /media/diskstation/[REMOVED] nfs rw,hard,intr,nolock 0 0
[REMOVED]:/volume1/[REMOVED] /media/diskstation/[REMOVED] nfs rw,hard,intr,nolock 0 0
[REMOVED]:/volume1/[REMOVED] /media/diskstation/[REMOVED] nfs rw,hard,intr,nolock 0 0
[REMOVED]:/volume1/[REMOVED] /media/diskstation/[REMOVED] nfs rw,hard,intr,nolock 0 0
[REMOVED]:/volume1/[REMOVED] /media/diskstation/[REMOVED] nfs rw,hard,intr,nolock 0 0
[REMOVED]:/volume1/[REMOVED] /media/diskstation/[REMOVED] nfs nouser,rw,hard,intr,nolock 0 0


---------- Current Mount Details of 'mount':
/dev/fuse on /run/user/1000/doc type fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/mapper/vgubuntu-root on / type ext4 (rw,relatime,errors=remount-ro)
/dev/nvme0n1p1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/nvme0n1p2 on /boot type ext4 (rw,relatime)
/dev/sda1 on /media/sda1 type ext4 (rw,relatime)

---------- USB Information from 'lsusb -t -v':
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 10000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 10000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/12p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 1: Dev 2, If 3, Class=Human Interface Device, Driver=usbhid, 12M
        ID 0c76:161f JMTek, LLC. 
    |__ Port 1: Dev 2, If 1, Class=Audio, Driver=snd-usb-audio, 12M
        ID 0c76:161f JMTek, LLC. 
    |__ Port 1: Dev 2, If 2, Class=Audio, Driver=snd-usb-audio, 12M
        ID 0c76:161f JMTek, LLC. 
    |__ Port 1: Dev 2, If 0, Class=Audio, Driver=snd-usb-audio, 12M
        ID 0c76:161f JMTek, LLC. 
    |__ Port 2: Dev 3, If 0, Class=Hub, Driver=hub/3p, 12M
        ID 413c:1003 Dell Computer Corp. Keyboard Hub
        |__ Port 1: Dev 5, If 1, Class=Human Interface Device, Driver=usbhid, 12M
            ID 413c:2010 Dell Computer Corp. Keyboard
        |__ Port 1: Dev 5, If 0, Class=Human Interface Device, Driver=usbhid, 12M
            ID 413c:2010 Dell Computer Corp. Keyboard
        |__ Port 2: Dev 7, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
            ID 04b3:3107 IBM Corp. ThinkPad 800dpi Optical Travel Mouse
        |__ Port 3: Dev 8, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
            ID 04b3:3107 IBM Corp. ThinkPad 800dpi Optical Travel Mouse
    |__ Port 7: Dev 4, If 0, Class=, Driver=, 12M
        ID 0639:7213 Chrontel, Inc. 
    |__ Port 10: Dev 6, If 0, Class=Wireless, Driver=btusb, 12M
        ID 8087:0026 Intel Corp. 
    |__ Port 10: Dev 6, If 1, Class=Wireless, Driver=btusb, 12M
        ID 8087:0026 Intel Corp. 

---------- Video Details from 'lshw':

  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list fb
       configuration: depth=32 driver=i915 latency=0 mode=2560x1440 visual=truecolor xres=2560 yres=1440
       resources: 
           iomemory:600-5ff 
           iomemory:400-3ff 
           irq:158 
           memory:6022000000-6022ffffff 
           memory:4000000000-400fffffff 
           ioport:3000(size=64) 
           memory:c0000-dffff

   --- Graphics Environment Continued from 'various graphics ENVs' ----
The Current Configured Destop is: ubuntu:GNOME 
The Current Desktop Session is: ubuntu 
The Current X Desktop Information Details from 'xrandr' are: 
Screen 0: minimum 320 x 200, current 4240 x 1440, maximum 16384 x 16384
DP-1 connected 1680x1050+2560+0 (normal left inverted right x axis y axis) 474mm x 296mm
DP-2 connected primary 2560x1440+0+0 (normal left inverted right x axis y axis) 698mm x 393mm
HDMI-1 disconnected (normal left inverted right x axis y axis)
The Current Session Type is: x11 
The Current Display Manager is: gdm3
The Current Desktop Theme: 'Yaru'
The Current Virtual TTYs being used are:
	TTY#	Used By
	tty2	gdm-x-session
	tty2	Xorg
	tty2	gnome-session-b

---------- Repository Information from '/etc/apt/sources.list and etc/apt/sources.list.d/':

Sources List:
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) focal main restricted
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) focal-updates main restricted
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) focal universe
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) focal-updates universe
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) focal multiverse
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) focal-updates multiverse
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse

Sources List from SourcesD:
/etc/apt/sources.list.d/atom.list:
deb [arch=amd64] [https://packagecloud.io/AtomEditor/atom/any/](https://packagecloud.io/AtomEditor/atom/any/) any main

---------- Other Details from 'Various':
The current kernel version is:       5.13.0-28-generic 
The current release description is:  Ubuntu 20.04.3 LTS 
Original Installation Date:          2022-01-08+11:43:21 
Original Installation Media: Ubuntu 20.04 LTS "Focal Fossa" - Release amd64 (20200423)
Do-Release-Upgrade Date: This system may have not had a 'Release Upgrade' through 'do-release-upgrade'

These are the current kernel ranges for HWE kernels for this release.
   --- HWE Kernel Reference from 'apt-cache show':
For HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.13.0.28.31
For HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.4.0.26.32

   --- HWE Package Status from 'dpkg':
Package linux-generic-hwe-20.04 is installed.

   --- Certified Hardware Platform Status: (By the Ubuntu Wiki Standards)
Ubuntu Certified Hardware Platform. Safe to install 
the Hardware Enablement Stack (HWE).

   --- User Installed Package List:
android-tools-adb		    nmap
apache2				    ntp
apache2-utils			    numlockx
apt-config-icons-hidpi		    okular
aptitude			    openscad
apulse				    p7zip
atom				    pastebinit
biglybt				    pavucontrol
chromium-browser		    php
clipit				    php-cli
curl				    php-curl
exfat-fuse			    php-gd
exfat-utils			    php-mbstring
fdupes				    php-mysql
filezilla			    php-tidy
geany				    php-xml
geeqie				    pngcrush
gimp				    printer-driver-cups-pdf
git				    proftpd-basic
gparted				    python-is-python2
gwenview			    qemu
hardinfo			    rar
htop				    screen
hwinfo				    ssh
lftp				    traceroute
lib32stdc++6			    ubuntu-restricted-extras
libminizip1			    unace
libnss3-tools			    unrar
lynx				    virtualbox
meld				    virtualbox-guest-additions-iso
mlocate				    vlc
mpg123				    vorbis-tools
mysql-server			    whois
net-tools			    xine-ui
netpbm				    youtube-dl
nfs-common			    yui-compressor
nfs-kernel-server

Currently logged in User(s):
NAME     LINE         TIME         COMMENT
yann     :0           Feb 12 09:48 (:0)

The User running this script was: yann
uid=1000(yann)
gid=1000(yann)
groups=1000(yann),4(adm),24(cdrom),27(sudo),30(dip),33(www-data),
46(plugdev),120(lpadmin),131(lxd),132(sambashare)

---- Required Programs For Report.
    All required programs installed for report. 

*** End Of Report ***

```

---

### Post by MAFoElffen on 2022-02-16
I have some tuning and tweak suggestions...

1. Update your BIOS Firmware. Your IOS is on version 5.16. Intel says the current version is 5.5.

2. Your Kingston SNVS 1000G NVMe firmware update software is only available for Windows OS... That may be a challenge to update on your computer.

3. Your system is installed on your NVMe driive, which is very fast, but is is installed on LVM, within LUKS encrytption. No problem with LVM, but with the extra security of the LUKS encryption, you do pay a price in performance, compared to if it where not encrypted. I don't really see that as a problem, as the speed of that drive with encryption... is still much higher than a SATA SSD (without encryption) and light years faster than a SATA HHD (without encryption).

4. You have Apache Web Server installed... Is it running in the background? How much websites are loaded and are they external or just for internal use and testing? Just wondering about the background load of... Is this for testing and/or dev work... Or system management? If so, I have some ideas for that, to make it use less resources... If not being used all the time, you can free the resource up by shutting it down...
```

sudo apachectl -k graceful-stop

```
5. You have 32GB RAM installed... But your swap is only set to 979MB(?) You have enough memory, that is it set not to ever go into suspend or hibernation it theoretically would be okay, unless it ever did, because it somehow shows that you are using 4GB of RAM, which is curious in itself... What is running and how are your memory and cpu resources being used?

Because if you are using 4GB at rest (the script doesn't take much to run), and if it goes to sleep, suspends., goes into hibernation, it will not fit into less than 1GB and = Crash.

That and even though it shows that you have over 25GB free, you are somehow paging into your swap and 2/3rds of it is being used...

Possibly making this bigger may improve your performance.. And will at least keep it from crashing if it ever goes to sleep, or goes into hibernation. Rule of thumb is 1.5 times the size of RAM. I usually give x2.

I would recommend shrinking the filesystem and LV of /dev/mapper/vgubunu-root, then grow vgubuntu-swap1. I would say to make the swap size 48 to 64 GB.

Those are the things that I see in the report results that would help "within" that computer.

---

### Post by TheFu on 2022-02-16
In my tests of LVM+LUKS on SATA SSDs, there is a 3% overhead.  For a portable system, like a laptop, the goodness outweighs the performance hit, IMHO.  Where a NUC lies on "portable" vs "desktop" depends on the location.  I don't encrypt storage on desktops and haven't encrypted storage for smaller (microITX or "shuttle") computers.  I have considered encrypting all storage as a rule, since 3% is a minor thing.

I can't tell what networking is being used. If wifi, I'd switch to any other method available. Wired, MoCA, or even powerline would be more stable, IME. This is critical for NFS.  wifi bandwidth, even in the best situations, fluctuates wildly. Humans don't see it, but computers do.  A stable 80Mbps is better than a fluctuating 300Mbps.

With 32G of RAM, I don't think the swap matters at all. I can't imagine anything running on a NUC that could use that RAM.  Suspend/sleep works fine with 4G swap on 8G of RAM systems. Just don't hibernate if your RAM exceeds swap.  But really, I think with that much RAM, you have the nearly ideal amount of swap. The old rules of thumb haven't applied in Unix since around 2002-ish as RAM sizes exploded.

I'm not thrilled with the LVM layout, but that shouldn't impact performance.

---

### Post by cactux on 2022-02-16
You are awesome, thanks a lot for all your contributions.

The Apache server is only for development of a web site, not accessed from external, only locally. As I am not always working on it, it makes sense to have it not started by default and start it only when needed.

The network connection is wired, even if wifi is configured. I guess that when both are available Linux choose the best one? Or should I deactivate the wifi?

I *will* come back here and update you of the results. As I'll apply the measures one by one, I hope I'll be able to point the decisive one (if there's one). It may take some time (wife, kids, etc... ;-) ) but I'll come back I promise.

If you think of something else, of course keep posting ;-)

Thanks and have a great day

---

### Post by TheFu on 2022-02-16
You should use rfkill to disable the wifi ... and bluetooth (assuming you care anything at all about security). Never use bluetooth.   NEVER.

---

