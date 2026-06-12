---
title: "Help for mounting raid partition"
date: 2016-08-22
forum: General Help
---

### Post by fvo on 2016-08-22
Hello,

I'm new to Linux.  I bought new hardware and installed Lubuntu 16.04 .  The Hardware has an Asus motherboard with two SSD (Samsung) and two Hard Drives (Western Digital).  Both the SSD and Hard Drives are mirrored are configured as Raid (LSI of motherboard).
I'm trying to use the Hard Drives now, but I don't find them, so I guess they are not mounted yet. Here comes my issue.... I don't know how to mount a Raid partition.

In the attachment some info from the Disks utility and the command   **lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL. **
In the Utility Disks,  the menu item "Edit Mount Options..."  is disabled.   

All above was done with user Root.

Many thanks for help,

Frank

---

### Post by SeijiSensei on 2016-08-22
Perhaps the megaraid driver isn't loading automatically.  Open a terminal and type the command "lsmod".  You should see some lines like this:
```

mptsas                 51992  3 
mptscsih               36638  1 mptsas
mptbase                93647  2 mptsas,mptscsih
scsi_transport_sas     35588  1 mptsas

```
If they don't appear then the driver isn't loaded. I don't know how to get the driver to load during installation on Ubuntu.  Perhaps someone else can help with this.  On my CentOS system with LSI Megaraid, the hardware was automatically detected and the driver configured to run at boot.  The pair of drives then appears as a single device, in my case /dev/sda.

You can also run "sudo lshw | more" then hit the space bar to page down through the lengthy output.  At some point you should see a stanza that looks something like this:
```

           *-scsi
                description: SCSI storage controller
                product: SAS1068E PCI-Express Fusion-MPT SAS
                vendor: LSI Logic / Symbios Logic
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: scsi0
                version: 08
                width: 64 bits
                clock: 33MHz
                capabilities: scsi pm pciexpress msi msix bus_master cap_list rom scsi-host
                configuration: driver=mptsas latency=0
                resources: irq:32 ioport:fc00(size=256) memory:df2ec000-df2effff memory:df2f0000-df2fffff memory:df100000-df1fffff(prefetch
able)

```
Worst case, you can reconfigure the LSI bios to treat each drive separately, then use [Linux software RAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID") to create the arrays.

---

### Post by fvo on 2016-08-22
I did the two commands  **sudo lshw | more ** and   **lsmod**. 

The output is the following

[B]sudo lshw | more
[/B]
[PHP]
     *-scsi:0
          physical id: 5
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Samsung SSD 840
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: CB6Q
             serial: S1DBNSBFB39882J
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=7fb983fd
           *-volume:0 UNCLAIMED
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                version: 1.0
                serial: 6abacb2f-0dbf-4bdc-9653-3878925df462
                size: 223GiB
                capacity: 223GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-08-19 10:48:22 filesystem=ext4 lastmountpoint=/ modified=2016-08-22 22:53:23 mounted=2016-08-22 22:53:23 state=clean
           *-volume:1 UNCLAIMED
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                size: 8152MiB
                capacity: 8152MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume UNCLAIMED
                   description: Linux swap / Solaris partition
                   physical id: 5
                   capacity: 8152MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 6
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Samsung SSD 840
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: CB6Q
             serial: S1DBNSBFB84456Z
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=7fb983fd
           *-volume:0 UNCLAIMED
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                version: 1.0
                serial: 6abacb2f-0dbf-4bdc-9653-3878925df462
                size: 223GiB
                capacity: 223GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-08-19 10:48:22 filesystem=ext4 lastmountpoint=/ modified=2016-08-22 22:53:23 mounted=2016-08-22 22:53:23 state=clean
           *-volume:1 UNCLAIMED
                description: Extended partition
                physical id: 2
                bus info: scsi@1:0.0.0,2
                size: 8152MiB
                capacity: 8152MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume UNCLAIMED
                   description: Linux swap / Solaris partition
                   physical id: 5
                   capacity: 8152MiB
                   capabilities: nofs
     *-scsi:2
          physical id: 7
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10EFRX-68F
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdc
             version: 0A82
             serial: WD-WCC4J6TV83VN
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=020941fd
           *-volume UNCLAIMED
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                version: 3.1
                serial: d6628fe5-6464-af46-9aa5-cc607b25b90b
                size: 930GiB
                capacity: 930GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2015-12-11 18:13:00 filesystem=ntfs label=New Volume state=clean
     *-scsi:3
          physical id: 8
          logical name: scsi3
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10EFRX-68F
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdd
             version: 0A82
             serial: WD-WCC4J3LDEJ02
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=020941fd
           *-volume UNCLAIMED
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@3:0.0.0,1
                version: 3.1
                serial: d6628fe5-6464-af46-9aa5-cc607b25b90b
                size: 930GiB
                capacity: 930GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2015-12-11 18:13:00 filesystem=ntfs label=New Volume state=clean
     *-scsi:4
          physical id: 9
          logical name: scsi5
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: BD-RE  BH20L
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: B57A
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
[/PHP]

[B]lsmod

[/B][PHP]
Module                  Size  Used by
ppdev                  20480  0
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             172032  0
kvm                   540672  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
serio_raw              16384  0
input_leds             16384  0
lpc_ich                24576  0
ipmi_ssif              24576  0
ipmi_si                57344  0
8250_fintek            16384  0
parport_pc             32768  0
parport                49152  2 ppdev,parport_pc
ipmi_msghandler        49152  2 ipmi_ssif,ipmi_si
mac_hid                16384  0
tpm_infineon           20480  0
ie31200_edac           16384  0
mei_me                 36864  0
shpchp                 36864  0
mei                    98304  1 mei_me
edac_core              53248  1 ie31200_edac
autofs4                40960  2
dm_mirror              24576  2
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  4 dm_region_hash,dm_mirror
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
psmouse               126976  0
ahci                   36864  4
libahci                32768  1 ahci
igb                   196608  0
ast                    61440  2
ttm                    94208  1 ast
dca                    16384  1 igb
ptp                    20480  1 igb
drm_kms_helper        147456  1 ast
pps_core               20480  1 ptp
i2c_algo_bit           16384  2 ast,igb
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   364544  5 ast,ttm,drm_kms_helper
video                  40960  0
fjes                   28672  0

[/PHP]
There is the following entry which looks like a raid service:    

dm_mirror                        24576  2
dm_region_hash         24576  1 dm_mirror

---

### Post by SeijiSensei on 2016-08-23
Are you sure you have configured the BIOS on the LSI device to create the arrays?  Linux clearly sees each drive as separate, and I don't think you have the driver loaded either.

It may be the driver is not bundled with the desktop version of Ubuntu since these devices are usually found on servers.  Some years back I ran a trial installation of Ubuntu Server 12.04 on the machine I manage with LSI RAID, and the installer discovered and configured the device correctly as did CentOS.  You might try booting from a [server disc]("http://www.ubuntu.com/download/server") and see if it identifies the RAID device.  You can always add a GUI desktop on top of the server installation.  

If you run "lspci" do you see something like this:
```
02:00.0 SCSI storage controller: LSI Logic / Symbios Logic SAS1068E PCI-Express Fusion-MPT SAS (rev 08)
```

I hope someone else chimes in here.  I don't have a lot more help I can offer.  You can Google for "lsi raid linux" or "lsi raid ubuntu".  You'll see a lot of documents on the subject.

---

