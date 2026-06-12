---
title: "Ubuntu EXTREMELY unstable. How to fix?"
date: 2013-05-30
forum: General Help
---

### Post by Karasawa7 on 2013-05-30
I had Ubuntu 13.04 on my laptop for the longest time (Around 3 months). This morning, Ubunutu kept popping up telling me some software needed updating (I just saw fonts, firefox updates, ect) Downloaded it. Next thing I know, computer froze. Restarted my computer, ubuntu logo is all jaged and pixely, go to my homepage, NOTHING works (wifi wasn't working, programs wouldn't open)

At this point, I told myself "13.04 is more or less a beta, let me just stick with 12.04"

So I put 12.04 on a disk, installed it on this laptop (opted to format the hardrive before installing 12.04)

12.04 installed nicely, got set up. Minecraft, Java, Skype (To talk to Fiance), etc.

I noticed that now I keep getting the dim screen (I'm assuming means not responding) on almost everything, and will randomly not respond until I close it, or close on its own for no reason. When ubuntu yelled at me saying I had to install a ton of little stuff, I get an error saying something went wrong, and now I can't install/remove software.

Please, tell me what the heck is going on. I didn't even do anything. Ubuntu is trying to do things to itself on both 13.04 and 12.04 and it's breaking itself >_>

(What prompted me to ask here is that I can't use skype for more than 10 minutes without it closeing randomly)

---

### Post by searchfgold6789 on 2013-05-30
Hmm... a variety of issues can cause this. 
The first thing you might try is a Memtest which you can select at boot. Let it run for 5 minutes, and if there are any errors, you probably need to replace one or more RAM modules.
The next thing I would try is to see if there are any graphics drivers you are missing. Open the Software Sources and go to the Additional Drivers tab to check.
Is your CPU overheating, perhaps? It happens a lot with laptops. Open Task Manager and see if there are any processes hogging CPU cycles, and make sure the bottom of the computer isn't getting too toasty or the fan is going too fast too often.
Providing us with a computer model or detailed hardware info would help us if there are any problems exclusive to your setup.

---

### Post by Karasawa7 on 2013-05-31
As for drivers, when you first install the OS and get it running, one of the first thing Ubuntu does is download ERRYTHING it thinks you need. Drivers, fonts, updates for this program, updates for that program. 252 items. (Keep in mind this is like, 15 minutes after formatting a harddrive and doing a clean install of a new OS). The laptop is a Dell Inspirion something something another. Just your run of the mill 2009 era laptop with an intel duo core processor and 2 gigs ram (DDR2 I believe).

The laptop is kept on a fan, and I'm certain it's not heat. I honestly think that (12.04) is freaking out now because I didn't get the opprotunity to install those updates, but I will apttempt to install the Additional Drivers stuff. 

I would really like to know why 13.04 completely bugged out on me though. I was really getting to love it. Too late now though, I've already wrote over it <_<.

Thank you good sir. I will attempt all of this in the morning as it's 3 in the morning. I will report back with the results of my efforts.

---

### Post by rrich1974 on 2013-05-31
i can tell you, on my inspiron 1521 from 2008 with only 1 GB of RAM, 12.04 and 13.04 works great. 
i suspect a hardware issue. 
run the "disk utility" and read the smart data of your HDD.

---

### Post by searchfgold6789 on 2013-05-31
+1 on checking the SMART status. Also, you are correct about Ubuntu being able to run smoothly on a 2009 dual core Inspiron, as well as the fact that there may be some changes in software updates that could solve your problem. If there is nothing in Additional Drivers, then you probably have an Intel GPU, and all of those are supported by the latest software. I would see whether or not installing all those updates and rebooting works, and if it doesn't, check memtest, SMART, and post back hardware details (like the output of sudo lshw), because there could be a specific piece of hardware that's slowing everything else down.

---

### Post by Karasawa7 on 2013-05-31
Ok. I ran memtest. 20 minutes, passed, no errors.
Another problem now. Every now and then when I boot, Ubuntu gives the error "Cannot locate disk drive /" I just press F to fix, and I guess it fixes it. Every few boots I have to do it. It's now been about 24 hours since I put 12.04 on here. 
As for sudo lshw... (It's really long <_<)

description: Portable Computer
    product: Inspiron 1750 ()
    vendor: Winbond Electronics
    serial: 5BMVRJ1
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=portable uuid=44454C4C-4200-104D-8056-B5C04F524A31
  *-core
       description: Motherboard
       product: 0F642T
       vendor: Winbond Electronics
       physical id: 0
       serial: .5BMVRJ1.CN7016699S01U6.
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A02
          date: 07/17/2009
          size: 64KiB
          capacity: 15MiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T6500  @ 2.10GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          slot: Microprocessor
          size: 1200MHz
          capacity: 2100MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 800 MHz (1.2 ns)
             product: M4 70T2864QZ3-CF7
             vendor: Samsung
             physical id: 0
             serial: 653BD050
             slot: DIMM_A
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR Synchronous 800 MHz (1.2 ns)
             product: M4 70T2864QZ3-CF7
             vendor: Samsung
             physical id: 1
             serial: 653BD04D
             slot: DIMM_B
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:46 memory:f6c00000-f6ffffff memory:e0000000-efffffff ioport:efe8(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f6b00000-f6bfffff
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6f60(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6f80(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:6fa0(size=32)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:22 memory:fed1c400-fed1c7ff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:47 memory:f6afc000-f6afffff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:80000000-801fffff ioport:80200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:f6900000-f69fffff ioport:80400000(size=2097152)
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g LP-PHY
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth2
                version: 01
                serial: 70:1a:04:16:86:08
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=192.168.0.106 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:17 memory:f69fc000-f69fffff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:d000(size=4096) memory:f6800000-f68fffff ioport:80600000(size=2097152)
           *-network
                description: Ethernet interface
                product: 88E8040 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 13
                serial: 00:25:64:63:23:86
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:45 memory:f68fc000-f68fffff ioport:de00(size=256)
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:c000(size=4096) memory:f6600000-f67fffff ioport:f0000000(size=2097152)
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6f00(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6f20(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:6f40(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:fed1c000-fed1c3ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:6e70(size=8) ioport:6e78(size=4) ioport:6e80(size=8) ioport:6e88(size=4) ioport:6ea0(size=32) memory:fed1c800-fed1cfff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f6afbf00-f6afbfff ioport:1100(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST9320325AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0003
             serial: 5VD1VQYF
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000cbb48
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: a196424d-0057-4b39-a0ad-62e6a70a0e52
                size: 296GiB
                capacity: 296GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-05-30 15:42:29 filesystem=ext4 lastmountpoint=/ modified=2013-05-31 15:30:34 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-05-31 15:31:27 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 2007MiB
                capacity: 2007MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2007MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD+-RW AD-7580S
             vendor: Optiarc
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: FD06
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@1:5
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
  *-battery
       product: DELL F965N98
       vendor: Sanyo
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 22500mWh
       configuration: voltage=14.4V

---

### Post by Karasawa7 on 2013-05-31
As for additional drivers, all my drivers are up to date and working according to it.

I think I should also add
sparks@sparks-Inspiron-1750:~$ df -Th
Filesystem            Type      Size  Used Avail Use% Mounted on
/dev/sda1             ext4      292G  8.7G  268G   4% /                                             (<----That's the one that Ubuntu keeps saying is missing.)
udev                  devtmpfs  970M  4.0K  970M   1% /dev
tmpfs                 tmpfs     393M  844K  392M   1% /run
none                  tmpfs     5.0M     0  5.0M   0% /run/lock
none                  tmpfs     982M  212K  982M   1% /run/shm
/home/sparks/.Private ecryptfs  292G  8.7G  268G   4% /home/sparks

---

### Post by Karasawa7 on 2013-05-31
The main problem is trying to install the 192 updates from the update manager. They're downladed and ready to install, however, midway through installation I get:

"An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks."

Click details, this is what's in details.

"Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 226, in _process_transaction
    self._apply_changes(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/pkcompat.py", line 2864, in _apply_changes
    install_range)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1007, in _apply_changes
    trans.output += inst_progress.output.decode(enc, "ignore")
  File "/usr/lib/python2.7/contextlib.py", line 35, in __exit__
    self.gen.throw(type, value, traceback)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1019, in _frozen_status
    shutil.rmtree(frozen_dir)
  File "/usr/lib/python2.7/shutil.py", line 250, in rmtree
    onerror(os.remove, fullname, sys.exc_info())
  File "/usr/lib/python2.7/shutil.py", line 248, in rmtree
    os.remove(fullname)
OSError: [Errno 30] Read-only file system: '/tmp/aptdaemon-frozen-status1laIAv/status'"

---

### Post by gordintoronto on 2013-06-01
Did you ever look at the SMART data? I would bet 10 to one that there is a hardware problem, and it's probably your hard drive.

---

### Post by mikeym on 2013-06-01
Could also conceivably  just be a bad download or burn. I'm not sure whether Ubuntu automatically checks the installation disk's checksum before installing or not. Definitely worth checking this before installing from another disk. 

[https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by searchfgold6789 on 2013-06-03
This definitely sounds like a classic hard disk problem to me, especially since you've tried multiple releases. It could be a bad DVD or iso file, but if that were the case you would be more likely to have problems during the actual installation. In any case, it would be advisable to back up any iportant data you have right away, and make sure things are OK with your hard disk in the Disk utility.

---

### Post by 3rdalbum on 2013-06-04
Check your SMART statistics first in Disk Utility.

If they turn out okay, run FSCK from a live CD.

Also, 20 minutes is not sufficient for a memory test. Run it for 12 hours.

---

### Post by txwooley on 2013-06-04
Smart Data doesn't always tell you the truth.  I ran into the exact same senario last year.  Laptop would work fine for a while but would hang if it needed to access the disk for any reason.  At start up it would occasionally complain of not finding a disk.  Checked the Smart Status and it said the Disk was healthy.  I didn't believe him and replaced the HDD.  No more problems.  I feel certain your problem is a bad HDD.

---

### Post by Karasawa7 on 2013-06-09
I just reinstalled Ubunutu 12.04 about 3 days ago. Works fine now. I think it was just a bad installation.

---

