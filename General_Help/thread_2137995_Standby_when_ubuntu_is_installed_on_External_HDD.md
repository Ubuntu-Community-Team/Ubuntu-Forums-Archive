---
title: "Standby when ubuntu is installed on External HDD"
date: 2013-04-22
forum: General Help
---

### Post by Yehonal on 2013-04-22
I've installed ubuntu on external HDD to move from a pc to another easily.

all things work like a charm :) but would be nice if i can fix the standby problem ( especially on notebook ) since after suspend notebook, it powers down the hard disk . So at resume it seems not recognized/loaded anymore and the console shows me a lot of ext4 write errors.

are there any solution to it?

---

### Post by Yehonal on 2013-04-23
bump.

my hp envy 15 , when is plugged to AC-power , doesn't halt my external hard disk and the suspension works as well.

[U]Instead on battery , it shutdowns the external hard disk ... when i resume suspension the usb seems that changes his device name from /dev/sdbX to /dev/sdcX
So the kernel try to use old sdbX device without success.[/U]

**i think** i need one of these solution:

**1) disable the power down of the external hard disk after suspension on battery mode.**

i've tried:
```
sudo sdparm --clear STANDBY -6 /dev/sdb 
``` 

but doesn't work

also tried :

 ```
acpitool -w 9
```

that shows
   ```
Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. SPB1      S4    *disabled  pci:0000:00:15.1
  2. OHC1      S3    *enabled   pci:0000:00:12.0
  3. OHC2      S3    *enabled   pci:0000:00:13.0
  4. OHC3      S3    *disabled  
  5. OHC4      S3    *disabled  
  6. EHC1      S3    *enabled   pci:0000:00:12.2
  7. EHC2      S3    *enabled   pci:0000:00:13.2
  8. EHC3      S3    *disabled  
  9. XHC0      S3    *disabled   pci:0000:00:10.0
  10. XHC1      S3    *disabled  
  11. KBC0      S3    *enabled   pnp:00:07
  12. PS2M      S3    *disabled  pnp:00:08
```

but the hard disk will be always halted

**2) second solution should be to force the external harddisk on /dev/sdb at resume instead changing it to sdc**

this solution would be very nice if working, because it can be power-safe too. 

this is the udev log for external hard disk:
```
UDEV  [18.698983] add      /devices/pci0000:00/0000:00:10.0/usb5/5-1/5-1:1.0/host2/target2:0:0/2:0:0:0/block/sdb/sdb3 (block)
ACTION=add
DEVLINKS=/dev/disk/by-id/ata-Samsung_SSD_840_Series_S14GNEACA39208Y-part3 /dev/disk/by-id/scsi-SSamsung_SSD_840_Series_801130168383-part3 /dev/disk/by-id/wwn-0x500253855001e044-part3 /dev/disk/by-path/pci-0000:00:10.0-usb-0:1:1.0-scsi-0:0:0:0-part3 /dev/disk/by-uuid/182a3188-283a-4e59-9a9f-917676fc5eef
DEVNAME=/dev/sdb3
DEVPATH=/devices/pci0000:00/0000:00:10.0/usb5/5-1/5-1:1.0/host2/target2:0:0/2:0:0:0/block/sdb/sdb3
DEVTYPE=partition
ID_ATA=1
ID_ATA_DOWNLOAD_MICROCODE=1
ID_ATA_FEATURE_SET_HPA=1
ID_ATA_FEATURE_SET_HPA_ENABLED=1
ID_ATA_FEATURE_SET_PM=1
ID_ATA_FEATURE_SET_PM_ENABLED=1
ID_ATA_FEATURE_SET_SECURITY=1
ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=2
ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=2
ID_ATA_FEATURE_SET_SMART=1
ID_ATA_FEATURE_SET_SMART_ENABLED=1
ID_ATA_ROTATION_RATE_RPM=0
ID_ATA_SATA=1
ID_ATA_SATA_SIGNAL_RATE_GEN1=1
ID_ATA_SATA_SIGNAL_RATE_GEN2=1
ID_ATA_WRITE_CACHE=1
ID_ATA_WRITE_CACHE_ENABLED=1
ID_BUS=ata
ID_FS_TYPE=swap
ID_FS_USAGE=other
ID_FS_UUID=182a3188-283a-4e59-9a9f-917676fc5eef
ID_FS_UUID_ENC=182a3188-283a-4e59-9a9f-917676fc5eef
ID_FS_VERSION=2
ID_MODEL=Samsung_SSD_840_Series
ID_MODEL_ENC=Samsung\x20SSD\x20840\x20Series\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
ID_PART_ENTRY_DISK=8:16
ID_PART_ENTRY_NUMBER=3
ID_PART_ENTRY_OFFSET=369766400
ID_PART_ENTRY_SCHEME=dos
ID_PART_ENTRY_SIZE=14374912
ID_PART_ENTRY_TYPE=0x82
ID_PART_TABLE_TYPE=dos
ID_PATH=pci-0000:00:10.0-usb-0:1:1.0-scsi-0:0:0:0
ID_PATH_TAG=pci-0000_00_10_0-usb-0_1_1_0-scsi-0_0_0_0
ID_REVISION=DXT06BQ0
ID_SCSI_COMPAT=SSamsung_SSD_840_Series_801130168383
ID_SERIAL=Samsung_SSD_840_Series_S14GNEACA39208Y
ID_SERIAL_SHORT=S14GNEACA39208Y
ID_TYPE=disk
ID_WWN=0x500253855001e044
ID_WWN_WITH_EXTENSION=0x500253855001e044
MAJOR=8
MINOR=19
SEQNUM=1589
SUBSYSTEM=block
UDEV_LOG=3
UDISKS_PARTITION=1
UDISKS_PARTITION_ALIGNMENT_OFFSET=0
UDISKS_PARTITION_NUMBER=3
UDISKS_PARTITION_OFFSET=189320396800
UDISKS_PARTITION_SCHEME=mbr
UDISKS_PARTITION_SIZE=7359954944
UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:10.0/usb5/5-1/5-1:1.0/host2/target2:0:0/2:0:0:0/block/sdb
UDISKS_PARTITION_TYPE=0x82
UDISKS_PRESENTATION_NOPOLICY=0
USEC_INITIALIZED=3515426
```

---

### Post by Yehonal on 2013-04-24
Bump.

Please help me a bit.

i'm trying some udev rule that should be applied at boot and when resum from suspension:

```
#first rename the sda if already exists
KERNEL=="sda?", ACTION==”add|change”, NAME="sdu%n"


#then change usb hard disk with static device name
SUBSYSTEMS=="block", ACTION==”add|change”, ENV{ID_SERIAL}=="Samsung_SSD_840_Series_S14GNEACA39208Y", KERNEL=="sd?", NAME="sda" 
SUBSYSTEMS=="block", ACTION==”add|change”, ENV{ID_FS_UUID}=="74498b3b-8047-469c-b8a1-4861994716d8", KERNEL=="sd?2", NAME="sda2"
SUBSYSTEMS=="block", ACTION==”add|change”, ENV{ID_FS_UUID}=="182a3188-283a-4e59-9a9f-917676fc5eef", KERNEL=="sd?3", NAME="sda3" 
SUBSYSTEMS=="block", ACTION==”add|change”, ENV{ID_SERIAL}=="Samsung_SSD_840_Series_S14GNEACA39208Y", KERNEL=="sd?4", NAME="sda4" 
SUBSYSTEMS=="block", ACTION==”add|change”, ENV{ID_FS_UUID}=="18AD134365C6AED2", KERNEL=="sd?5", NAME="sda5" 
```

but it doesn't work...where am i doing wrong? is there another solution?

---

### Post by Yehonal on 2013-04-26
> **Yehonal said:**
> Bump.

Please help me a bit.

i'm trying some udev rule that should be applied at boot and when resum from suspension:

```
#first rename the sda if already exists
KERNEL=="sda?", ACTION==”add|change”, NAME="sdu%n"


#then change usb hard disk with static device name
SUBSYSTEMS=="block", ACTION==”add|change”, ENV{ID_SERIAL}=="Samsung_SSD_840_Series_S14GNEACA39208Y", KERNEL=="sd?", NAME="sda" 
SUBSYSTEMS=="block", ACTION==”add|change”, ENV{ID_FS_UUID}=="74498b3b-8047-469c-b8a1-4861994716d8", KERNEL=="sd?2", NAME="sda2"
SUBSYSTEMS=="block", ACTION==”add|change”, ENV{ID_FS_UUID}=="182a3188-283a-4e59-9a9f-917676fc5eef", KERNEL=="sd?3", NAME="sda3" 
SUBSYSTEMS=="block", ACTION==”add|change”, ENV{ID_SERIAL}=="Samsung_SSD_840_Series_S14GNEACA39208Y", KERNEL=="sd?4", NAME="sda4" 
SUBSYSTEMS=="block", ACTION==”add|change”, ENV{ID_FS_UUID}=="18AD134365C6AED2", KERNEL=="sd?5", NAME="sda5" 
```

but it doesn't work...where am i doing wrong? is there another solution?

BUMP.

after renamed 10-local.rules to z99-local.rules , it works.. but doesn't solve my problem


please reply my simple question: is not possible to standby ubuntu when installed on usb?

---

