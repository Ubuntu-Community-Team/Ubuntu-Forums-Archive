---
title: "ongoing Ubuntu 14.04 will not boot"
date: 2014-12-20
forum: General Help
---

### Post by okkie2 on 2014-12-20
I have a disk with Ubuntu 14.04 lts. I have done three complete reinstalls the past week that will not boot the next day or two. The last one with no updates. Is it my bios settings or has it got anything to do with my system,which is very up to date as far as I know and with four gigg memory.I have never encoutered this over the years. Can somebody for some reason do this to a computer  like in my case ? sorry for thinking this way but it is all I have left.What causes the boot problems and how can it be prevented. In retrospect, that has been the only problem I had with Ubuntu over the years.
Thanks

---

### Post by ajgreeny on 2014-12-20
This could be a UEFI problem [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) but without more info on your hardware it is impossible to know where you have got to and what went wrong.
Two things would be useful:-
1 - Tell us what hardware you have or show us the output of terminal command sudo lshw copied here in code-tags (see my signature below for code-tags how-to info)
2 - Have a look at Boot-Repair, also in my signature, and copy back here the pastebin link you will get from running the boot-info script.

---

### Post by sudodus on 2014-12-20
There might be a problem with your hardware, for example the RAM or the hard disk drive.

---

### Post by okkie2 on 2014-12-22
Here is the outcome of sudo lshw. I was about to use the install disk/try ubuntu when I realised that my system booted out of the blue by itself during the night.I hope this is not a joke.
I thought I have once again lost everything but notice that I have more than one partition. Could my documents etc. still be on one of them and can it be rescued?
I also have 'boot repair' on a USB stick.How can I put it to work and make part of my system to prevent the 'no boot' problem?
Thanks a lot.```
okkie@okkie-MS-7788:~$ sudo lshw
[sudo] password for okkie: 
okkie-ms-7788             
    description: Desktop Computer
    product: MS-7788 (To be filled by O.E.M.)
    vendor: MSI
    version: 1.0
    serial: To be filled by O.E.M.
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=To be filled by O.E.M. uuid=00000000-0000-0000-0000-D43D7E50FC85
  *-core
       description: Motherboard
       product: H61M-S20 (G3) (MS-7788)
       vendor: MSI
       physical id: 0
       version: 1.0
       serial: To be filled by O.E.M.
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: V1.8
          date: 11/07/2012
          size: 64KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cache:0
          description: L2 cache
          physical id: 3c
          slot: CPU Internal L2
          size: 512KiB
          capacity: 512KiB
          capabilities: internal write-through unified
     *-cache:1
          description: L1 cache
          physical id: 3d
          slot: CPU Internal L1
          size: 128KiB
          capacity: 128KiB
          capabilities: internal write-through data
     *-cache:2
          description: L3 cache
          physical id: 3e
          slot: CPU Internal L3
          size: 3MiB
          capacity: 3MiB
          capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 3f
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1333 MHz (0,8 ns)
             product: SRT4G86U0-H9H
             vendor: 8783
             physical id: 0
             serial: 16240600
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 1
             serial: [Empty]
             slot: ChannelA-DIMM1
        *-bank:2
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 2
             serial: [Empty]
             slot: ChannelB-DIMM0
        *-bank:3
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 3
             serial: [Empty]
             slot: ChannelB-DIMM1
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) CPU G645 @ 2.90GHz
          vendor: Intel Corp.
          physical id: 40
          bus info: cpu@0
          version: Intel(R) Pentium(R) CPU G645 @ 2.90GHz
          slot: SOCKET 0
          size: 2700MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer xsave lahf_lm arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 threads=2
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:42 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:41 memory:f7c08000-f7c0800f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7c06000-f7c063ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:43 memory:f7c00000-f7c03fff
        *-pci:0
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:e000(size=4096) ioport:f0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 05
                serial: d4:3d:7e:50:fc:85
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:40 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7c05000-f7c053ff
        *-isa
             description: ISA bridge
             product: H61 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f110(size=8) ioport:f100(size=4) ioport:f0f0(size=8) ioport:f0e0(size=4) ioport:f0d0(size=16) ioport:f0c0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7c04000-f7c040ff ioport:f040(size=32)
        *-ide:1
             description: IDE interface
             product: 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f070(size=16) ioport:f060(size=16)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GH22NS70
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: EX01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST31000528AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: CC46
             serial: 9VPAXV53
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000a53ce
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: 364cc7ee-12bb-42af-bd36-f9961dc60feb
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable extended_attributes ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/boot modified=2014-12-22 16:25:07 mount.fstype=ext2 mount.options=rw,relatime mounted=2014-12-22 16:25:07 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                size: 931GiB
                capacity: 931GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux LVM Physical Volume partition
                   physical id: 5
                   logical name: /dev/sda5
                   serial: cCzlBu-A8Fi-rZ6T-i4BA-kE63-DlU1-ATOnLV
                   size: 931GiB
                   capacity: 931GiB
                   capabilities: multi lvm2
     *-scsi:2
          physical id: 3
          bus info: usb@2:1.3
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             configuration: sectorsize=512
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
okkie@okkie-MS-7788:~$
```

---

### Post by sudodus on 2014-12-22
It looks like you installed a system with LVM and encrypted disk. I think the 243MiB ext2 file system is the /boot partition. If this is the case, you should have two logins: a passphrase for the encrypted disk and a password to log into the linux desktop. Or did you select LVM without encrypted disk?

From the grub menu you can run memtest to check you RAM.

You can check the S.M.A.R.T. status of the hard disk drive and look for possible errors.

But it can be software problems.

---

### Post by okkie2 on 2014-12-23
Thanks for your reply.
My first install was in fact encripted and lvm.I am just not sure what my password was anymore. Is there a way I can determine this or change it in some way?
I have vital documents on the encripted system which I badly need.

---

### Post by sudodus on 2014-12-23
The whole idea with encryption is that the data should available only with the passphrase and/or password. You have to stretch your memory and try all passwords that you recall having used (and variations of them).

---

### Post by okkie2 on 2014-12-23
Thanks,
I think it is the same as I am using now so it automatically boots the new system where I opted not to log in with my password.
Is there a terminal code I can use to tell the computer to boot the system I first loaded and which ended up not booting. I need to get the problem system to boot but now have no way to get to it. At least we know it is still on the hard disk.

---

### Post by sudodus on 2014-12-23
Please boot from a live drive (USB/DVD/CD) and post the output of the following command

```
sudo parted -l
```

... space minus ell

Then try mount the partitions on the internal drive (as many as possible) and post the output of the following command

```
df
```

It will tell a little more about the computer's partitions.

---

### Post by okkie2 on 2014-12-24
I logged in with the install disk 'try Ubuntu' and here is the output of the above commands```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   1000GB  1000GB  extended
 5      257MB   1000GB  1000GB  logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 4178MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  4178MB  4178MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 996GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  996GB  996GB  ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/cow             1967236   45616   1921620   3% /
udev             1955680       4   1955676   1% /dev
tmpfs             393448    1216    392232   1% /run
/dev/sr0         1004544 1004544         0 100% /cdrom
/dev/loop0        961280  961280         0 100% /rofs
none                   4       0         4   0% /sys/fs/cgroup
tmpfs            1967236       4   1967232   1% /tmp
none                5120       4      5116   1% /run/lock
none             1967236      76   1967160   1% /run/shm
none              102400      48    102352   1% /run/user
ubuntu@ubuntu:~$
```

---

### Post by sudodus on 2014-12-24
You have only one system on this internal drive (Model: ATA ST31000528AS).

What parted sees is the original partitions and the LVM mappers for swap and root partitions of the installed system.

The only other drive is the live drive
```
/dev/sr0         1004544 1004544         0 100% /cdrom
```

When you install systems like this, it will grab the whole disk (and overwrite what was there before).

---

### Post by okkie2 on 2014-12-26
To summarise then, I have Ubuntu 14.04 installed and it boots normally.No encription and I am srarting right from the beginning? What I have learned the hard way and considdering what I lost in the process over the years, is that an external drive is a absolute must, and the only sure way to save information. It should actually be recommended to newbies as ,with my experience, they will one day have a non booting system and 'initramfs' command line, from where I have never had a successful recovery.

Thanks for your assistance

---

### Post by sudodus on 2014-12-26
You are right. We are many people who have learned the hard way to make backups, at least before installation of operating systems, at best as a regular habit :-P

I added a few lines about backup at the beginning of this link [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

