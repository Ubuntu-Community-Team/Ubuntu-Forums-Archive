---
title: "How to mount SD card?"
date: 2017-11-24
forum: General Help
---

### Post by 007casper on 2017-11-24
How to mount SD card? 

The SD card is formatted already in I think exfat32.  I have inserted in my friend's old pc, it reads it. 

I have inserted in my old xp laptop, and SD card doesnt show up.

I have tried multiple things for the SD to mount on ubuntu 17.10... no luck.

Please, advise. Thank you



```
root@puter:/# sudo apt-get install exfat-utils exfat-fuse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
exfat-fuse is already the newest version (1.2.7-1).
exfat-utils is already the newest version (1.2.7-1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

change ownership
root@puter:/# cd media
root@puter:/media# ls -al
total 12
drwxr-xr-x   3 root root 4096 Jun  5 00:01 .
drwxr-xr-x  24 root root 4096 Nov 24 18:14 ..
drwxr-x---+  2 o    o    4096 Nov 20 20:12 o
```

it doesnt show up when you do fdisk either
root@puter:/media# sudo fdisk -l

---

### Post by DuckHook on 2017-11-24
exfat is not supported by any of the 'buntus by default because it is a MS proprietary closed-source format.

You can run exfat in user-space through FUSE.```
sudo apt install exfat-fuse exfat-utils
```Be sure to reboot. Any exfat partition should automount after that.

---

### Post by 007casper on 2017-11-24
```
sudo apt install exfat-fuse exfat-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
exfat-fuse is already the newest version (1.2.7-1).
exfat-utils is already the newest version (1.2.7-1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@puter:/media# tail -f /var/log/syslog
Nov 24 19:10:55 puter gnome-shell[5820]: [AppIndicatorSupport-WARN] Attempting to re-register :1.67/org/ayatana/NotificationItem/multiload; resetting instead
Nov 24 19:10:55 puter gnome-shell[5820]: [AppIndicatorSupport-WARN] Item :1.67/org/ayatana/NotificationItem/multiload is already registered
Nov 24 19:10:55 puter dhclient[18498]: DHCPREQUEST of 192.168.0.101 on wlp3s0 to 192.168.0.254 port 67 (xid=0x1f22f452)
Nov 24 19:10:55 puter dhclient[18498]: DHCPACK of 192.168.0.101 from 192.168.0.254
Nov 24 19:10:55 puter NetworkManager[4396]: <info>  [1511579455.3994] dhcp4 (wlp3s0):   address 192.168.0.101
Nov 24 19:10:55 puter NetworkManager[4396]: <info>  [1511579455.3995] dhcp4 (wlp3s0):   plen 24 (255.255.255.0)
Nov 24 19:10:55 puter NetworkManager[4396]: <info>  [1511579455.3995] dhcp4 (wlp3s0):   gateway 192.168.0.254
Nov 24 19:10:55 puter NetworkManager[4396]: <info>  [1511579455.3995] dhcp4 (wlp3s0):   lease time 60
Nov 24 19:10:55 puter NetworkManager[4396]: <info>  [1511579455.3995] dhcp4 (wlp3s0):   nameserver '192.168.0.254'
Nov 24 19:10:55 puter NetworkManager[4396]: <info>  [1511579455.3996] dhcp4 (wlp3s0): state changed bound -> bound
Nov 24 19:10:55 puter dbus[4356]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Nov 24 19:10:55 puter systemd[1]: Starting Network Manager Script Dispatcher Service...
Nov 24 19:10:55 puter dhclient[18498]: bound to 192.168.0.101 -- renewal in 28 seconds.
Nov 24 19:10:55 puter dbus[4356]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Nov 24 19:10:55 puter systemd[1]: Started Network Manager Script Dispatcher Service.
Nov 24 19:10:55 puter nm-dispatcher: req:1 'dhcp4-change' [wlp3s0]: new request (2 scripts)
Nov 24 19:10:55 puter nm-dispatcher: req:1 'dhcp4-change' [wlp3s0]: start running ordered scripts...
Nov 24 19:10:55 puter nm-dispatcher[15665]: Error: missing function library \'/usr/share/tlp/tlp-functions\'.
Nov 24 19:10:55 puter nm-dispatcher: req:1 'dhcp4-change' [wlp3s0], "/etc/NetworkManager/dispatcher.d/99tlp-rdw-nm": complete: failed with Script '/etc/NetworkManager/dispatcher.d/99tlp-rdw-nm' exited with error status 1.
Nov 24 19:10:55 puter NetworkManager[4396]: <warn>  [1511579455.4287] dispatcher: (3949) 99tlp-rdw-nm failed (failed): Script '/etc/NetworkManager/dispatcher.d/99tlp-rdw-nm' exited with error status 1.
Nov 24 19:10:55 puter gnome-shell[5820]: [AppIndicatorSupport-WARN] Attempting to re-register :1.67/org/ayatana/NotificationItem/multiload; resetting instead
Nov 24 19:10:55 puter gnome-shell[5820]: [AppIndicatorSupport-WARN] Item :1.67/org/ayatana/NotificationItem/multiload is already registered
```

---

### Post by DuckHook on 2017-11-24
As a follow-up, since I didn't read your output thoroughly the first time, you appear to have activated your root account. I sure hope you know what you are doing, because this is not recommended practice for Ubuntu. Use sudo instead. You won't get into s much trouble.

In any case, what this means for you is: don't go mounting things in root. Mount to your user account only. Otherwise, you won't be able to access it from your user account.

Last but not least: please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by DuckHook on 2017-11-24
We crossed posted.

Don't use root! Try it from your user account. And please use [CODE] tags.

---

### Post by 007casper on 2017-11-24
Cheers. I am still trying to make the SD card mount.  It sure shows up on windows 10.

```
sudo apt install exfat-fuse exfat-utils
```

no luck.

---

### Post by DuckHook on 2017-11-24
> **007casper said:**
> …It sure shows up on windows 10.
I should think that it would. It's MS own product so is built right into their kernel. In Linux, the drivers can't be included in the kernel because it would taint the kernel. Therefore, it has to be added as a user action.
> ```
sudo apt install exfat-fuse exfat-utils
```

no luck.From your previous output, for some reason, these packages already existed on your system. There's no further need to add them. Did you add them earlier? Please provide full account of everything you did prior to requesting help on the forums.

Did you do what I asked in post #5?

---

### Post by 007casper on 2017-11-24
I did exit from root.  Still no luck. 

I shut down and reboot... no luck

Strange.

```
sun@puter:~$ sudo apt install exfat-fuse exfat-utils
[sudo] password for o: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
exfat-fuse is already the newest version (1.2.7-1).
exfat-utils is already the newest version (1.2.7-1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by DuckHook on 2017-11-24
As stated, your system already has these apps installed. There is no point in installing them again.

If you still cannot mount your SD card, then try mounting it manually. Instructions here: [https://www.howtogeek.com/235655/how-to-mount-and-use-an-exfat-drive-on-linux/](https://www.howtogeek.com/235655/how-to-mount-and-use-an-exfat-drive-on-linux/)

You can also try taking the SD card out and plugging it back in again.

Make sure everything is done from a user account only using sudo. Installing while operating as the root account is fraught with problems. It may subsequently allow access only to root.

---

### Post by 007casper on 2017-11-25
Thanks for the link but something is wrong here.  I had this issue while back with exfat SD card and was able to make it work before.
So, I was surprised that it couldnt read this card. 

```
sudo apt-get install exfat-fuse exfat-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
exfat-fuse is already the newest version (1.2.7-1).
exfat-utils is already the newest version (1.2.7-1).


``` 

I am familiar with root.  I usually go to root level as a last resort.

In any case, I read somewhere that nvidia driver could be the issue and there is a bug. So, I tried to purge 
nvidia driver, and update etc... and the system will just hang.

So, I went to root level and purge nvidia drivers. Then, I upgrade, update, clean, autoremove etc. Still it didnt work.

I tried to see the drive and mount manually. However, the SD card doesnt even show up when you do fdisk.

---

### Post by DuckHook on 2017-11-25
The *apt-get install* command only installs the utilities. Since you now have them installed, it won't help to try installing them again. They are already there. The output you are posting simply confirms this. It is pointless to keep trying *apt-get install*.

The problem seems to be either with your SD card itself or with the system's ability to read it. In other words, it is less likely to be a problem with the driver or the exfat subsystem (though this cannot be ruled out either).

Please post output from the following:```
df -h
``````
sudo blkid
``````
sudo parted -l
``````
sudo lshw -C disk -short
``````
sudo lshw -C volume -short
```

---

### Post by 007casper on 2017-11-26
I have inserted the SD card again.  Then, ran the commands on the terminal as a regular user.

```

 df -h
Filesystem        Size  Used Avail Use% Mounted on
udev              7.8G     0  7.8G   0% /dev
tmpfs             1.6G  166M  1.4G  11% /run
/dev/nvme0n1p2     22G  5.7G   16G  28% /
tmpfs             7.8G  101M  7.7G   2% /dev/shm
tmpfs             5.0M  4.0K  5.0M   1% /run/lock
tmpfs             7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/nvme0n1p1    511M  4.6M  507M   1% /boot/efi
/dev/nvme0n1p3    430G  393G   16G  97% /home
tmpfs             1.6G   16K  1.6G   1% /run/user/126
tmpfs             1.6G   23M  1.6G   2% /run/user/1000
/home/sun/.Private  430G  393G   16G  97% /home/sun


sudo blkid
[sudo] password for sun: 
/dev/nvme0n1: PTUUID="49f6a93c-1846-4d58-b404-f5bb2b80a47a" PTTYPE="gpt"
/dev/nvme0n1p1: UUID="479E-CB72" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="c7c20e90-debe-4c6a-a0e8-ad47d3f07e44"
/dev/nvme0n1p2: UUID="98d21473-fd21-4493-8ac8-3dd52cfee241" TYPE="ext4" PARTUUID="ef718c85-110c-4004-940e-3350d2488c5e"
/dev/nvme0n1p3: UUID="d044f11d-cecd-4c98-986e-b8e0210e91c5" TYPE="ext4" PARTUUID="27aa727a-fa83-4233-97be-14b82a3eb0fc"
/dev/nvme0n1p4: UUID="435b7c8f-9b45-4dc8-8938-6d5515c7d717" TYPE="swap" PARTUUID="57a4bad0-a431-4b86-bd8b-1f6873e56b51"
/dev/mapper/cryptswap1: UUID="4c9bd4c5-2334-4e68-8799-9d493508634c" TYPE="swap"


 sudo parted -l
Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 17.6GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  17.6GB  17.6GB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/nvme0n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  538MB   537MB   fat32           EFI System Partition  boot, esp
 2      538MB   24.5GB  24.0GB  ext4
 3      24.5GB  495GB   470GB   ext4
 4      495GB   512GB   17.6GB  linux-swap(v1)


 sudo lshw -C disk -short
H/W path       Device  Class          Description
=================================================


sudo lshw -C volume -short
H/W path       Device  Class          Description
=================================================



```

---

### Post by DuckHook on 2017-11-26
Your OS thinks that no SD card exists. You already knew this, but that's why exfat utilities don't work: they don't see anything to work *with*.

lshw is designed to reveal all system hardware. The fact that it returns nothing with regard to disks or volumes is very odd. Please post```
sudo lshw -short
```Hopefully, by asking it to show everything, we will see what your system looks like. Also, if the output with the *-short* flag is not long, then post the output of:```
sudo lshw -sanitize
```Be prepared for a lengthy output. We are trying to see whether your system recognizes the SD card at all.

I should have asked this before, but how is the SD card connected? Is it through a USB reader? If so, please post output of:```
lsusb
```

Unrelated, but you should also have a look at your /home directory. It is 97% full, which leaves you no room for any further growth and causes file fragmentation even with as efficient a file system as ext4. You should try to never let your disk space fill beyond 85%.

---

### Post by 007casper on 2017-11-27
I totally agree, slowly I have been transferring files. I should definitely not go above 85% hard drive space.

```

sun@puter:~$ sudo lshw -short
[sudo] password for sun: 
H/W path       Device  Class          Description
=================================================
                       system         N501VW (ASUS-NotebookSKU)
/0                     bus            N501VW
/0/0                   memory         64KiB BIOS
/0/12                  memory         128KiB L1 cache
/0/13                  memory         128KiB L1 cache
/0/14                  memory         1MiB L2 cache
/0/15                  memory         6MiB L3 cache
/0/16                  processor      Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz
/0/17                  memory         16GiB System Memory
/0/17/0                memory         8GiB SODIMM DDR4 Synchronous 2133 MHz (0.5
/0/17/1                memory         [empty]
/0/17/2                memory         8GiB SODIMM DDR4 Synchronous 2133 MHz (0.5
/0/17/3                memory         [empty]
/0/100                 bridge         Skylake Host Bridge/DRAM Registers
/0/100/1               bridge         Skylake PCIe Controller (x16)
/0/100/1/0             display        GM107M [GeForce GTX 960M]
/0/100/2               display        HD Graphics 530
/0/100/4               generic        Skylake Processor Thermal Subsystem
/0/100/14              bus            Sunrise Point-H USB 3.0 xHCI Controller
/0/100/14/0    usb1    bus            xHCI Host Controller
/0/100/14/0/4          multimedia     USB2.0 HD UVC WebCam
/0/100/14/0/9          communication  Bluetooth wireless interface
/0/100/14/0/c          input          SiS HID Touch Controller
/0/100/14/1    usb2    bus            xHCI Host Controller
/0/100/14/1/6          generic        USB 10/100/1000 LAN
/0/100/14.2            generic        Sunrise Point-H Thermal subsystem
/0/100/15              generic        Sunrise Point-H Serial IO I2C Controller #
/0/100/15.1            generic        Sunrise Point-H Serial IO I2C Controller #
/0/100/16              communication  Sunrise Point-H CSME HECI #1
/0/100/17              storage        Sunrise Point-H SATA Controller [AHCI mode
/0/100/1c              bridge         Sunrise Point-H PCI Express Root Port #2
/0/100/1c/0            generic        Alcor Micro
/0/100/1c.2            bridge         Sunrise Point-H PCI Express Root Port #3
/0/100/1c.2/0  wlp3s0  network        Wireless 7265
/0/100/1c.4            bridge         Sunrise Point-H PCI Express Root Port #5
/0/100/1d              bridge         Sunrise Point-H PCI Express Root Port #9
/0/100/1d/0            storage        NVMe SSD Controller SM951/PM951
/0/100/1f              bridge         Sunrise Point-H LPC Controller
/0/100/1f.2            memory         Memory controller
/0/100/1f.3            multimedia     Sunrise Point-H HD Audio
/0/100/1f.4            bus            Sunrise Point-H SMBus
/1             eth0    network        Ethernet interface


```

```

sun@puter:~$ sudo lshw -sanitize
computer                    
    description: Notebook
    product: N501VW (ASUS-NotebookSKU)
    vendor: ASUSTeK COMPUTER INC.
    version: 1.0
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 smp vsyscall32
    configuration: boot=normal chassis=notebook family=N sku=ASUS-NotebookSKU uuid=[REMOVED]
  *-core
       description: Motherboard
       product: N501VW
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: 1.0
       serial: [REMOVED]
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: N501VW.300
          date: 05/09/2016
          size: 64KiB
          capacity: 5952KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification uefi
     *-cache:0
          description: L1 cache
          physical id: 12
          slot: L1 Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back data
          configuration: level=1
     *-cache:1
          description: L1 cache
          physical id: 13
          slot: L1 Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back instruction
          configuration: level=1
     *-cache:2
          description: L2 cache
          physical id: 14
          slot: L2 Cache
          size: 1MiB
          capacity: 1MiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:3
          description: L3 cache
          physical id: 15
          slot: L3 Cache
          size: 6MiB
          capacity: 6MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz
          vendor: Intel Corp.
          physical id: 16
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz
          serial: [REMOVED]
          slot: U3E1
          size: 3191MHz
          capacity: 4005MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
          configuration: cores=4 enabledcores=4 threads=8
     *-memory
          description: System Memory
          physical id: 17
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: SODIMM DDR4 Synchronous 2133 MHz (0.5 ns)
             product: Ve
             vendor: Micron
             physical id: 0
             serial: [REMOVED]
             slot: ChannelA-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
        *-bank:1
             description: [empty]
             physical id: 1
             slot: ChannelA-DIMM1
        *-bank:2
             description: SODIMM DDR4 Synchronous 2133 MHz (0.5 ns)
             product: HMA41GS6AFR8N-TF
             vendor: SK Hynix
             physical id: 2
             serial: [REMOVED]
             slot: ChannelB-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
        *-bank:3
             description: [empty]
             physical id: 3
             slot: ChannelB-DIMM1
     *-pci
          description: Host bridge
          product: Skylake Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=skl_uncore
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Skylake PCIe Controller (x16)
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:e000(size=4096) memory:dc000000-dd0fffff ioport:b0000000(size=301989888)
           *-display
                description: 3D controller
                product: GM107M [GeForce GTX 960M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:125 memory:dc000000-dcffffff memory:b0000000-bfffffff memory:c0000000-c1ffffff ioport:e000(size=128) memory:dd000000-dd07ffff
        *-display
             description: VGA compatible controller
             product: HD Graphics 530
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:126 memory:db000000-dbffffff memory:70000000-7fffffff ioport:f000(size=64) memory:c0000-dffff
        *-generic:0
             description: Signal processing controller
             product: Skylake Processor Thermal Subsystem
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:16 memory:dd420000-dd427fff
        *-usb
             description: USB controller
             product: Sunrise Point-H USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:122 memory:dd410000-dd41ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.13.0-17-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.13
                capabilities: usb-2.00
                configuration: driver=hub slots=16 speed=480Mbit/s
              *-usb:0
                   description: Video
                   product: USB2.0 HD UVC WebCam
                   vendor: 04081-0009490016291005773
                   physical id: 4
                   bus info: usb@1:4
                   version: 0.03
                   serial: [REMOVED]
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:1
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: 9
                   bus info: usb@1:9
                   version: 0.01
                   capabilities: bluetooth usb-2.01
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
              *-usb:2
                   description: Human interface device
                   product: SiS HID Touch Controller
                   vendor: USBest Technology
                   physical id: c
                   bus info: usb@1:c
                   version: 2.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.13.0-17-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.13
                capabilities: usb-3.00
                configuration: driver=hub slots=8 speed=5000Mbit/s
              *-usb
                   description: Generic USB device
                   product: USB 10/100/1000 LAN
                   vendor: Realtek
                   physical id: 6
                   bus info: usb@2:6
                   version: 30.00
                   serial: [REMOVED]
                   capabilities: usb-3.00
                   configuration: driver=r8152 maxpower=256mA speed=5000Mbit/s
        *-generic:1
             description: Signal processing controller
             product: Sunrise Point-H Thermal subsystem
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:18 memory:dd438000-dd438fff
        *-generic:2
             description: Signal processing controller
             product: Sunrise Point-H Serial IO I2C Controller #0
             vendor: Intel Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:16 memory:dd437000-dd437fff
        *-generic:3
             description: Signal processing controller
             product: Sunrise Point-H Serial IO I2C Controller #1
             vendor: Intel Corporation
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:17 memory:dd436000-dd436fff
        *-communication
             description: Communication controller
             product: Sunrise Point-H CSME HECI #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:124 memory:dd435000-dd435fff
        *-storage
             description: SATA controller
             product: Sunrise Point-H SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 31
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:123 memory:dd430000-dd431fff memory:dd434000-dd4340ff ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:dd433000-dd4337ff
        *-pci:1
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #2
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:dd300000-dd3fffff
           *-generic UNCLAIMED
                description: Unassigned class
                product: Alcor Micro
                vendor: Alcor Micro
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:dd300000-dd3000ff
        *-pci:2
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 memory:dd200000-dd2fffff
           *-network
                description: Wireless interface
                product: Wireless 7265
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 59
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.13.0-17-generic firmware=29.541020.0 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:135 memory:dd200000-dd201fff
        *-pci:3
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:c4000000-da0fffff ioport:80000000(size=570425344)
        *-pci:4
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #9
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:d000(size=4096) memory:dd100000-dd1fffff
           *-storage
                description: Non-Volatile memory controller
                product: NVMe SSD Controller SM951/PM951
                vendor: Samsung Electronics Co Ltd
                physical id: 0
                bus info: pci@0000:3d:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress msix nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:16 memory:dd100000-dd103fff ioport:d000(size=256)
        *-isa
             description: ISA bridge
             product: Sunrise Point-H LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 31
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory UNCLAIMED
             description: Memory controller
             product: Sunrise Point-H PMC
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 31
             width: 32 bits
             clock: 33MHz (30.3ns)
             capabilities: bus_master
             configuration: latency=0
             resources: memory:dd42c000-dd42ffff
        *-multimedia
             description: Audio device
             product: Sunrise Point-H HD Audio
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:127 memory:dd428000-dd42bfff memory:dd400000-dd40ffff
        *-serial UNCLAIMED
             description: SMBus
             product: Sunrise Point-H SMBus
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 31
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:dd432000-dd4320ff ioport:f040(size=32)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: [REMOVED]
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.09.9 duplex=full ip=[REMOVED] link=yes multicast=yes port=MII speed=1Gbit/s


```


```

sun@puter:~$ lsusb
Bus 002 Device 003: ID 0bda:8153 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:0a2a Intel Corp. 
Bus 001 Device 002: ID 0bda:57f6 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0457:11d1 Silicon Integrated Systems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



```

---

### Post by DuckHook on 2017-11-27
Okay, I think I took you on an unnecessary detour. You have an NVMe SSD which doesn't show up as a conventional disk to Ubuntu, so all of the lshw reports show that you have no disk. No worries. All is good, but lshw isn't going to be of much help to us.

With the SD card plugged in, please post output of```
lsblk
```We're getting closer.

Time to ask for more in-depth info.

[LIST]
[*]What USB adapter do you use?
[*]What brand and model SD card?
[*]You mention that it works in your friend's old pc, but what OS is your friend running?
[*]When it worked before, was it the same SD card or another?
[*]Was it the same USB adapter or another?
[/LIST]
Boot up without the SD card (make sure it's *not* inserted) and type:```
dmesg | tail -n 30
```
..record this info to any text file. Then insert the card and without doing anything further run the above code again. Record its output to a different file. Post both results (before and after) back to this thread. The tail command returns just the last 30 lines of dmesg. dmesg itself is supposed to tell us what state changes are happening to your system. Therefore the two together should show what happens when you insert the SD card.

---

### Post by 007casper on 2017-11-28
```
sun@puter:~$ lsblk
NAME           MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
nvme0n1        259:0    0   477G  0 disk  
&#9500;&#9472;nvme0n1p1    259:1    0   512M  0 part  /boot/efi
&#9500;&#9472;nvme0n1p2    259:2    0  22.4G  0 part  /
&#9500;&#9472;nvme0n1p3    259:3    0 437.7G  0 part  /home
&#9492;&#9472;nvme0n1p4    259:4    0  16.4G  0 part  
  &#9492;&#9472;cryptswap1 253:0    0  16.4G  0 crypt [SWAP]

```

    **What USB adapter do you use?**
What do you mean? USB adapter? The SD adapter is build in. I dont use any external usb adapters to access the SD card.  This SD card is the old looking kind. It isnt a micro card.  
My laptop has an SD card reader build in. I dont know the type or manufacturer of the SD card reader.

   ** What brand and model SD card?**
SanDisk Extreme Pro 95 MB/s - SDXC UHS-I Card

    **You mention that it works in your friend's old pc, but what OS is your friend running?**
Hardware - Inspiron 3847
OS Edition - Windows 10 Home
OS Build - 15063.726
System Type - 64 bit Operating system x64 based processor 

His computer is really slow and full of virus, malware you name it. I really dont want to 
use his computer to access the files.  I just inserted to see if it will read and I accessed a few random files, and it worked flawlessly.

   ** When it worked before, was it the same SD card or another?**
It was another SD card. Not the same one. Also, it was previous version of the ubuntu, I think it was 16.04 when it worked, not 17.10
Right now, I am on 17.10.

    **Was it the same USB adapter or another?**
HIs computer is a desktop and I think it came with the "Inspiron 3847".  It has an SD card reader, and dont know the type.


Boot up without the SD card
```
sun@puter:~$ dmesg | tail -n 30
[   15.124417] wlp3s0: send auth to a4:2b:b0:20:5a:dc (try 1/3)
[   15.149645] wlp3s0: authenticated
[   15.152102] wlp3s0: associate with a4:2b:b0:20:5a:dc (try 1/3)
[   15.166275] wlp3s0: RX AssocResp from a4:2b:b0:20:5a:dc (capab=0xc11 status=0 aid=5)
[   15.168223] wlp3s0: associated
[   15.168297] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[   26.130656] Could not find key with description: [0fb51aa7594bee97]
[   26.130659] process_request_key_err: No key
[   26.130659] Could not find valid key in user session keyring for sig specified in mount option: [0fb51aa7594bee97]
[   26.130661] One or more global auth toks could not properly register; rc = [-2]
[   26.130662] Error parsing options; rc = [-2]
[   27.265731] Bluetooth: RFCOMM TTY layer initialized
[   27.265743] Bluetooth: RFCOMM socket layer initialized
[   27.265752] Bluetooth: RFCOMM ver 1.11
[   27.616116] usb 2-6: new SuperSpeed USB device number 2 using xhci_hcd
[   27.636693] usb 2-6: New USB device found, idVendor=0bda, idProduct=8153
[   27.636694] usb 2-6: New USB device strings: Mfr=1, Product=2, SerialNumber=6
[   27.636695] usb 2-6: Product: USB 10/100/1000 LAN
[   27.636696] usb 2-6: Manufacturer: Realtek
[   27.636696] usb 2-6: SerialNumber: 000001000000
[   27.768653] usbcore: registered new interface driver r8152
[   27.772796] usbcore: registered new interface driver cdc_ether
[   27.892283] usb 2-6: reset SuperSpeed USB device number 2 using xhci_hcd
[   27.945752] r8152 2-6:1.0 eth0: v1.09.9
[   27.948295] r8152 2-6:1.0 enx00e04c60dbdb: renamed from eth0
[   27.982381] IPv6: ADDRCONF(NETDEV_UP): enx00e04c60dbdb: link is not ready
[   27.987692] IPv6: ADDRCONF(NETDEV_UP): enx00e04c60dbdb: link is not ready
[   28.093657] rfkill: input handler disabled
[   31.284482] r8152 2-6:1.0 enx00e04c60dbdb: carrier on
[   31.284510] IPv6: ADDRCONF(NETDEV_CHANGE): enx00e04c60dbdb: link becomes ready

```

Then inserted the SD card
```

sun@puter:~$ dmesg | tail -n 30
[   15.124417] wlp3s0: send auth to a4:2b:b0:20:5a:dc (try 1/3)
[   15.149645] wlp3s0: authenticated
[   15.152102] wlp3s0: associate with a4:2b:b0:20:5a:dc (try 1/3)
[   15.166275] wlp3s0: RX AssocResp from a4:2b:b0:20:5a:dc (capab=0xc11 status=0 aid=5)
[   15.168223] wlp3s0: associated
[   15.168297] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[   26.130656] Could not find key with description: [0fb51aa7594bee97]
[   26.130659] process_request_key_err: No key
[   26.130659] Could not find valid key in user session keyring for sig specified in mount option: [0fb51aa7594bee97]
[   26.130661] One or more global auth toks could not properly register; rc = [-2]
[   26.130662] Error parsing options; rc = [-2]
[   27.265731] Bluetooth: RFCOMM TTY layer initialized
[   27.265743] Bluetooth: RFCOMM socket layer initialized
[   27.265752] Bluetooth: RFCOMM ver 1.11
[   27.616116] usb 2-6: new SuperSpeed USB device number 2 using xhci_hcd
[   27.636693] usb 2-6: New USB device found, idVendor=0bda, idProduct=8153
[   27.636694] usb 2-6: New USB device strings: Mfr=1, Product=2, SerialNumber=6
[   27.636695] usb 2-6: Product: USB 10/100/1000 LAN
[   27.636696] usb 2-6: Manufacturer: Realtek
[   27.636696] usb 2-6: SerialNumber: 000001000000
[   27.768653] usbcore: registered new interface driver r8152
[   27.772796] usbcore: registered new interface driver cdc_ether
[   27.892283] usb 2-6: reset SuperSpeed USB device number 2 using xhci_hcd
[   27.945752] r8152 2-6:1.0 eth0: v1.09.9
[   27.948295] r8152 2-6:1.0 enx00e04c60dbdb: renamed from eth0
[   27.982381] IPv6: ADDRCONF(NETDEV_UP): enx00e04c60dbdb: link is not ready
[   27.987692] IPv6: ADDRCONF(NETDEV_UP): enx00e04c60dbdb: link is not ready
[   28.093657] rfkill: input handler disabled
[   31.284482] r8152 2-6:1.0 enx00e04c60dbdb: carrier on
[   31.284510] IPv6: ADDRCONF(NETDEV_CHANGE): enx00e04c60dbdb: link becomes ready




```

---

### Post by DuckHook on 2017-11-28
> **007casper said:**
> The SD adapter is build in. I dont use any external usb adapters to access the SD card.
My bad. Should have caught that before. *lshw* turned out to be not so useless after all. Your SD reader is given in this section in your lshw report:
```
           *-generic UNCLAIMED
                description: Unassigned class
                product: Alcor Micro
                vendor: Alcor Micro
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:dd300000-dd3000ff
```
With that clue and further research, I found this related thread: [https://ubuntuforums.org/showthread.php?t=2375885](https://ubuntuforums.org/showthread.php?t=2375885)
&#8230;you are not alone. It seems that the Alcor Micro card reader is problematic with some kernels.
> ** When it worked before, was it the same SD card or another?**
It was another SD card. Not the same one. Also, it was previous version of the ubuntu, I think it was 16.04 when it worked, not 17.10
Right now, I am on 17.10.
I'm guessing that the kernel you are running under 17.10 does not have the Alcor driver compiled, whereas your old Xenial install did. It's just a guess, but it would account for what we are seeing from your various reports. When *dmesg* doesn't change with the insertion of the SD card, this means that the OS does not even see the most basic state change in your HW. This is usually due to the driver being absent, and not a misconfiguration or other higher level issue.

At this point, my advice would be the following steps:

[LIST=1]
[*]Try out a LiveUSB of Xenial.
[*]Can the card be seen in Xenial? You only need to see it. Your specific card can't be read without the exfat suite of utilities.
[*]If Xenial works, then you must make a choice. Either reinstall Xenial, which is a LTS and is, frankly, a better choice for general users anyways over standard releases like Aardvark, or
[*]Work around the lack of an Alcor driver by using a USB SD card adapter. Mine is from Sandisk, and they are cheap and reliable.
[/LIST]
If the card reader is usable in Xenial, then my honest advice would be to bite the bullet and reinstall Xenial. I'm of the opinion that its a mistake for general users to flock to standard releases. They are less stable, less tested, less reliable, and lead to the sort of problems that you are experiencing now. However, you may already have so much invested in your current install that the best way is to work around your problem with a USB adapter which, after all, is a simple and pain-free work-around.

Only you can decide which way you want to go.

---

### Post by sudodus on 2017-11-29
> **DuckHook said:**
> My bad. Should have caught that before. *lshw* turned out to be not so useless after all. Your SD reader is given in this section in your lshw report:
```
           *-generic UNCLAIMED
                description: Unassigned class
                product: Alcor Micro
                vendor: Alcor Micro
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:dd300000-dd3000ff
```
With that clue and further research, I found this related thread: [https://ubuntuforums.org/showthread.php?t=2375885](https://ubuntuforums.org/showthread.php?t=2375885)
…you are not alone. It seems that the Alcor Micro card reader is problematic with some kernels.

I'm guessing that the kernel you are running under 17.10 does not have the Alcor driver compiled, whereas your old Xenial install did. It's just a guess, but it would account for what we are seeing from your various reports. When *dmesg* doesn't change with the insertion of the SD card, this means that the OS does not even see the most basic state change in your HW. This is usually due to the driver being absent, and not a misconfiguration or other higher level issue.

At this point, my advice would be the following steps:

[LIST=1]
[*]Try out a LiveUSB of Xenial.
[*]Can the card be seen in Xenial? You only need to see it. Your specific card can't be read without the exfat suite of utilities.
[*]If Xenial works, then you must make a choice. Either reinstall Xenial, which is a LTS and is, frankly, a better choice for general users anyways over standard releases like Aardvark, or
[*]Work around the lack of an Alcor driver by using a USB SD card adapter. Mine is from Sandisk, and they are cheap and reliable.
[/LIST]
If the card reader is usable in Xenial, then my honest advice would be to bite the bullet and reinstall Xenial. I'm of the opinion that its a mistake for general users to flock to standard releases. They are less stable, less tested, less reliable, and lead to the sort of problems that you are experiencing now. However, you may already have so much invested in your current install that the best way is to work around your problem with a USB adapter which, after all, is a simple and pain-free work-around.

Only you can decide which way you want to go.

+1

I agree with this advice :-)

---

### Post by jerrylaz on 2017-11-29
I solved a similar issue with sd cards that failed to mount on 16.04.  I have multiple Canon cameras.  Each sd card was formatted with the camera as per Canon.  They all failed to mount.  I no longer have the problem.  Here is what I did and how I tested it.  I used gparted to solve the issue.

1. Using gparted I deleted the partition after placing the sd card in the slot of my Dell computer.  I then created a new partition and formatted "using any fat".
2,  I unmounted the sd card, placed it in the camera and took a photo.
3.  I could see the photo on the lcd of the camera.
4.  I place the sd card in the slot in the computer.  It mounted and I could see the photo on my display.
5   I did the same thing with the remaining sd cards that had the same issue.

Everything works well.  You will probably lose the photos you had on he card.  You might be able to recover them with photorec.

---

### Post by DuckHook on 2017-11-29
> **jerrylaz said:**
> I solved a similar issue…
Thanks for contributing, but your situation is quite different than the OP's. Your system could see your SD card. That's why gparted could work on it. You had a partition incompatible with Linux and repartitioning it was an option. The OP cannot see his/her SD card at all because the card reader is missing its driver (or so we surmise), ergo gparted won't even be able to see the card to work on it.

---

### Post by Eric Davelaar on 2017-12-21
I often cannot mount an SD card, usually because I used another card first and have not rebooted; after reboot the card mounts immediately.
Not having the time to reboot just now or to continue trying suggestions found online so I had a look using the Disks utility and saw the card listed; ejected it and it went off the llist; re-inserted it and it was there again but not mounting. I used Disks 'eject' function, removed and re-inserted the card and it mounted right away.
Hope this helps someone!

---

