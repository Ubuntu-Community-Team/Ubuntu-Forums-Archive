---
title: "Unusual DVD drive  problem"
date: 2008-07-02
forum: General Help
---

### Post by sobepmp on 2008-07-02
I was able to install Ubuntu from the dvd drive and i can boot a live cd from it but it  doessn't recognnize any other cd or dvd I put in.  I searched the forum but I couldn't find an answer to this problem.

---

### Post by VMC on 2008-07-02
> **sobepmp said:**
> I was able to install Ubuntu from the dvd drive and i can boot a live cd from it but it  doessn't recognnize any other cd or dvd I put in.  I searched the forum but I couldn't find an answer to this problem.

Can you clarify. It doesn't recognize the cd using the installed ubuntu or putting in another boot cd your computer doesn't recognize it.

---

### Post by harshpshah on 2008-07-02
I have a similar problem. I just installed ubuntu hardy 2 days ago, it recognizes all the cds I put in, but it doesn't recognize any DVD's that I put in. I searched the forums and most of the questions I found was how to get DVD video working. My DVDs are data backups. It's most important that I can access them. The same DVD recognizes perfectly fine in the vmware windows xp, so it's not my drive. Ubuntu mounts the dvd but when i double click on the dvd icon, the folder is empty.


More info if you need:
dell 6400 laptop.
ubuntu hardy
windows xp on vmware server (where dvds can be read)
I have libdvd installed.
My dvds were created on windows system. I don't think I used any option that said it would only be run on windows. Used Roxio 6 to create dvds.

---

### Post by VMC on 2008-07-02
Type this into a Terminal

```
wodim -checkdrive
```

---

### Post by harshpshah on 2008-07-04
> **VMC said:**
> Type this into a Terminal

```
wodim -checkdrive
```

This is the output from the above command, I don't know what that means.

Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
Error trying to open /dev/cdrom exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrom exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrom exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrom exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrom exclusively (Device or resource busy)... giving up.
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

---

### Post by VMC on 2008-07-04
Did you try what it was asking? Here's what mine reported:

> vmc@vmc-desktop:~$ wodim -scanbus
scsibus1:
	1,0,0	100) 'HL-DT-ST' 'DVD-RAM GSA-H22N' '1.01' Removable CD-ROM
	1,1,0	101) *
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *
vmc@vmc-desktop:~$ wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'	rwrw-- : 'HL-DT-ST' 'DVD-RAM GSA-H22N'
-------------------------------------------------------------------------

It looks like your dvd drive is not detected. How is it setup through the BIOS?

---

### Post by harshpshah on 2008-07-07
> **VMC said:**
> Did you try what it was asking? Here's what mine reported:


It looks like your dvd drive is not detected. How is it setup through the BIOS?


Ok, found a workaround, but I don't like it. If I open nautilus as root (sudo nautilus), then navigate to the DVD drive, I can see the files there and even open them, copy them etc. But why do I have to open nautilus as root every time to access DVD? are there any rights/permissions I can setup?

Thanks for the help.

---

### Post by ChameleonDave on 2008-07-07
> **sobepmp said:**
> I was able to install Ubuntu from the dvd drive and i can boot a live cd from it but it  doessn't recognnize any other cd or dvd I put in.  I searched the forum but I couldn't find an answer to this problem.

Please enter the following command into a terminal:

```

cat /etc/fstab

```

The following might conceivably be useful too:
```

sudo blkid
ls -l /dev/scd* /dev/cd* /dev/dvd*

```

---

### Post by ChameleonDave on 2008-07-08
Please paste (in code tags, please!!!) the output of the following command:

```

sudo lshw -sanitize -C disk

```

This and the other ones may give us information that allows us to fix your problem.

---

### Post by sobepmp on 2008-07-10
It doesn't recognize the cd using the installed ubuntu.  I can boot from alive cd. 

> **VMC said:**
> Type this into a Terminal

```
wodim -checkdrive
```

user@user-desktop:~$ wodim -checkdrive
Device was not specified. Trying to find an appropriate drive...
Using drive: /dev/scd0
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'MAD DOG '
Identification : 'MD-16XDVD9      '
Revision       : '2.FC'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
user@user-desktop:~$ 

[QUOTE]=ChameleonDave;5334819]Please enter the following command into a terminal:

```

cat /etc/fstab

```
user@user-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=270bc6a6-1698-4068-8103-907ce9793bb7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=dfd39ad8-f490-407f-a901-7968634867b2 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
user@user-desktop:~$ 

> **ChameleonDave said:**
> Please paste the output of the following command:

```

sudo lshw -sanitize

```

user@user-desktop:~$ sudo lshw -sanitize
[sudo] password for user: 
computer                  
    description: Desktop Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=0
  *-core
       description: Motherboard
       product: LP NF4 Series
       vendor: DFI Corp,LTD
       physical id: 0
       version: 1.0
       slot: Internal Cache
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (07/06/2005)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot
     *-cpu:0
          description: CPU
          product: Dual Core AMD Opteron(tm) Processor 170
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: Dual Core AMD Opteron(tm) Processor 170
          slot: Socket 939
          size: 2010MHz
          capacity: 3GHz
          width: 64 bits
          clock: 201MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow rep_good pni lahf_lm cmp_legacy
        *-cache:0
             description: L1 cache
             physical id: b
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: d
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back
     *-cpu:1
          description: CPU
          vendor: AMD
          physical id: 5
          bus info: cpu@1
          version: Dual Core AMD Opteron(tm) Processor 170
          slot: Socket 939
          size: 2010MHz
          capacity: 3GHz
          clock: 201MHz
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: e
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM [empty]
             physical id: 0
             slot: A0
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
             width: 64 bits
        *-bank:2
             description: DIMM
             physical id: 2
             slot: A2
             size: 1GiB
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: CK804 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3 module=i2c_nforce2
     *-usb:0
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-multimedia
          description: Multimedia audio controller
          product: CK804 AC'97 Audio Controller
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          logical name: scsi4
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
        *-cdrom
             description: SCSI CD-ROM
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/scd0
             logical name: /dev/sr0
             capabilities: audio
             configuration: status=ready
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: scsi1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-disk
             description: ATA Disk
             product: MAXTOR STM350063
             vendor: Maxtor
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: 3.AA
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000b4c57
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                logical name: /dev/.static/dev
                version: 1.0
                serial: [REMOVED]
                size: 462GiB
                capacity: 462GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                configuration: created=2008-04-02 17:14:42 filesystem=ext3 modified=2008-07-07 14:42:39 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-07-07 14:42:39 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                size: 2941MiB
                capacity: 2941MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2941MiB
                   capabilities: nofs
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master
        *-firewire
             description: FireWire (IEEE 1394)
             product: IEEE 1394 Host Controller
             vendor: VIA Technologies, Inc.
             physical id: 9
             bus info: pci@0000:01:09.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=32 module=ohci1394
        *-network
             description: Ethernet interface
             product: 88E8001 Gigabit Ethernet Controller
             vendor: Marvell Technology Group Ltd.
             physical id: a
             bus info: pci@0000:01:0a.0
             logical name: eth1
             version: 13
             serial: [REMOVED]
             size: 100MB/s
             capacity: 1GB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=[REMOVED] latency=32 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=100MB/s
     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a3
          serial: [REMOVED]
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
     *-pci:1
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:4
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-display
             description: VGA compatible controller
             product: G71 [GeForce 7950 GT]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:05:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress vga_controller bus_master cap_list
             configuration: driver=nvidia latency=0 module=nvidia
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
user@user-desktop:~$

---

### Post by ChameleonDave on 2008-07-10
Sobepmp, try this.

Open your fstab file for editing with any *one* of the following commands:

```

sudo nano /etc/fstab
gksudo gedit /etc/fstab
kdesudo kwrite /etc/fstab

```

Disable the line starting with "/dev/hda" by putting a hash sign ("#") in front of it.

Then, add the following line after it:

```

/dev/scd0  /media/cdrom1  udf,iso9660  rw,user,noauto,exec  0  0

```

Save, and close the editor.

Make sure that the mount-point exists, with this command:

```

sudo mkdir /media/cdrom1

```

Insert a disc, and try to mount it with the following command:

```

mount /dev/scd0

```

---

### Post by sobepmp on 2008-07-11
Thanx that helped, I amable to play music cds ok.  I don't seem to be able to mount data cds though.  I get a message "mount: block device /dev/scd0 is write-protected, mounting read-only"

---

### Post by mc4man on 2008-07-11
How many cd/dvd drives do you have?
It may be informative if you put a data cd in the drive and run 
```
sudo lshw -C disk
```

---

### Post by ChameleonDave on 2008-07-12
> **sobepmp said:**
> Thanx that helped, I amable to play music cds ok.  I don't seem to be able to mount data cds though.  I get a message "mount: block device /dev/scd0 is write-protected, mounting read-only"
That's not an error.  It is correct for CDs to be mounted read-only.

---

### Post by sobepmp on 2008-07-12
I have one DVD.

user@user-desktop:~$ sudo lshw -C disk
[sudo] password for user: 
  *-cdrom                 
       description: SCSI CD-ROM
       product: MD-16XDVD9
       vendor: MAD DOG
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 2.FC
       serial: [MAD DOG MD-16XDVD9      2.FC05013100
       capabilities: removable audio
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
  *-disk
       description: ATA Disk
       product: MAXTOR STM350063
       vendor: Maxtor
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 9QG80JRX
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000b4c57
user@user-desktop:~$

---

### Post by sobepmp on 2008-07-12
> **ChameleonDave said:**
> That's not an error.  It is correct for CDs to be mounted read-only.OK but not able to access the data on the cds with this PC.

---

### Post by mc4man on 2008-07-12
Did you have a _data cd_ in the drive when you ran lshw.....?
what it's showing is media in the drive but no filesystem detected, hence
> configuration: ansiversion=5 status=ready
*-medium
physical id: 0
logical name: /dev/cdrom1
That's what you'd expect to see from either an audio cd or blank cd/dvd media

---

### Post by sobepmp on 2008-07-12
> **mc4man said:**
> Did you have a _data cd_ in the drive when you ran lshw.....?
what it's showing is media in the drive but no filesystem detected, hence

That's what you'd expect to see from either an audio cd or blank cd/dvd mediaYes I had a data cd in the drive.  My laptop can read the data on the same cd just fine.

---

### Post by mc4man on 2008-07-12
> My laptop can read the data on the same cd just fine. what Os is on the laptop?

while it's likely to show the same as the data cd do you have something with a known filesystem like a commercial dvd you can insert and the run the lshw.... again.
Also run after inserting some media  ```
dmesg | tail
```
While your at it go into fstab and delete the /dev/hda line you commented.

Note on fstab
In terms of your cd/dvd drive fstab 'ties' the device to a mount point with specific options, as far as the ability to mount the filesystem at all it's irrelevant. For instance if i went into my fstab and deleted the line for the dvd drive i could still autoplay/play dvds, access data cd/dvds, play audio cds. The ease of use and functionality of apps would be affected, but as far as mounting itself, no.

---

### Post by ChameleonDave on 2008-07-12
> **sobepmp said:**
> OK but not able to access the data on the cds with this PC.
Are you sure?

I mean, the "mounting read-only" message indicates that the disc was successfully mounted.  Immediately after receiving such a message, it would be good to do "ls -l /media/cdrom1" to see if you can list the contents of the disc.

---

### Post by sobepmp on 2008-07-15
> **ChameleonDave said:**
> Are you sure?

I mean, the "mounting read-only" message indicates that the disc was successfully mounted.  Immediately after receiving such a message, it would be good to do "ls -l /media/cdrom1" to see if you can list the contents of the disc.
user@user-desktop:~$ ls -l /media/cdrom1
total 0
user@user-desktop:~$ 



When I put the cd in my laptop with Windows Vista I can see the files.

---

