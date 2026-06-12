---
title: "Knowing what drive each drivetemp is for"
date: 2023-08-13
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2023-08-13
```
[FONT=monospace][COLOR=#000000]$ sensors drivetemp-* [/COLOR]
drivetemp-scsi-10-0 
Adapter: SCSI adapter 
temp1:        +35.0°C  (low  =  +0.0°C, high = +65.0°C) 
                       (crit low = -41.0°C, crit = +85.0°C) 
                       (lowest = +28.0°C, highest = +38.0°C) 

drivetemp-scsi-8-0 
Adapter: SCSI adapter 
temp1:        +35.0°C  (low  =  +0.0°C, high = +65.0°C) 
                       (crit low = -41.0°C, crit = +85.0°C) 
                       (lowest = +27.0°C, highest = +38.0°C) 

drivetemp-scsi-4-0 
Adapter: SCSI adapter 
temp1:        +51.0°C  (low  =  +0.0°C, high = +100.0°C) 
                       (crit low =  +0.0°C, crit = +100.0°C) 
                       (lowest = +31.0°C, highest = +55.0°C) 

drivetemp-scsi-0-0 
Adapter: SCSI adapter 
temp1:        +48.0°C  (low  =  +0.0°C, high = +100.0°C) 
                       (crit low =  +0.0°C, crit = +100.0°C) 
                       (lowest = +30.0°C, highest = +58.0°C) 

drivetemp-scsi-12-0 
Adapter: SCSI adapter 
temp1:        +36.0°C  (low  =  +0.0°C, high = +65.0°C) 
                       (crit low = -41.0°C, crit = +85.0°C) 
                       (lowest = +28.0°C, highest = +38.0°C) 

drivetemp-scsi-9-0 
Adapter: SCSI adapter 
temp1:        +35.0°C  (low  =  +0.0°C, high = +65.0°C) 
                       (crit low = -41.0°C, crit = +85.0°C) 
                       (lowest = +27.0°C, highest = +37.0°C) 

drivetemp-scsi-5-0 
Adapter: SCSI adapter 
temp1:        +51.0°C  (low  =  +0.0°C, high = +100.0°C) 
                       (crit low =  +0.0°C, crit = +100.0°C) 
                       (lowest = +30.0°C, highest = +55.0°C) 

drivetemp-scsi-1-0 
Adapter: SCSI adapter 
temp1:        +52.0°C  (low  =  +0.0°C, high = +100.0°C) 
                       (crit low =  +0.0°C, crit = +100.0°C) 
                       (lowest = +33.0°C, highest = +55.0°C)
[/FONT]
```
```
[FONT=monospace][COLOR=#000000]$ ls -l /dev/disk/by-id|grep -v part [/COLOR]
total 0 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 ata-INTEL_SSDSCKKF128G8_SATA_128GB_BTLA810613SC128I -> ../../sdc 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 ata-INTEL_SSDSCKKF128G8_SATA_128GB_BTLA810616PX128I -> ../../sdd 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 ata-INTEL_SSDSCKKF128G8_SATA_128GB_BTLA81061ECP128I -> ../../sda 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 ata-INTEL_SSDSCKKF128G8_SATA_128GB_BTLA81510DU3128I -> ../../sdb 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 ata-WDC_WD40EFRX-68N32N0_WD-WCC7K0CSZY00 -> ../../sde 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 ata-WDC_WD40EFRX-68N32N0_WD-WCC7K0RY7R37 -> ../../sdg 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 ata-WDC_WD40EFRX-68N32N0_WD-WCC7K4PE4C1U -> ../../sdh 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 ata-WDC_WD40EFRX-68N32N0_WD-WCC7K7KKNSN9 -> ../../sdf 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 md-name-ubuntu-server:0 -> ../../md0 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 md-name-ubuntu-server:1 -> ../../md1 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 md-uuid-28843301:920a306f:47f8cd80:d4d35fcd -> ../../md1 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 md-uuid-ede07d21:4114781a:b6762645:db22bf0e -> ../../md0 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-0ATA_INTEL_SSDSCKKF12_BTLA810613SC128I -> ../../sdc 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-0ATA_INTEL_SSDSCKKF12_BTLA810616PX128I -> ../../sdd 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-0ATA_INTEL_SSDSCKKF12_BTLA81061ECP128I -> ../../sda 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-0ATA_INTEL_SSDSCKKF12_BTLA81510DU3128I -> ../../sdb 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-0ATA_WDC_WD40EFRX-68N_WD-WCC7K0CSZY00 -> ../../sde 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-0ATA_WDC_WD40EFRX-68N_WD-WCC7K0RY7R37 -> ../../sdg 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-0ATA_WDC_WD40EFRX-68N_WD-WCC7K4PE4C1U -> ../../sdh 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-0ATA_WDC_WD40EFRX-68N_WD-WCC7K7KKNSN9 -> ../../sdf 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-1ATA_INTEL_SSDSCKKF128G8_SATA_128GB_BTLA810613SC128I -> ../../sdc 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-1ATA_INTEL_SSDSCKKF128G8_SATA_128GB_BTLA810616PX128I -> ../../sdd 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-1ATA_INTEL_SSDSCKKF128G8_SATA_128GB_BTLA81061ECP128I -> ../../sda 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-1ATA_INTEL_SSDSCKKF128G8_SATA_128GB_BTLA81510DU3128I -> ../../sdb 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-1ATA_WDC_WD40EFRX-68N32N0_WD-WCC7K0CSZY00 -> ../../sde 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-1ATA_WDC_WD40EFRX-68N32N0_WD-WCC7K0RY7R37 -> ../../sdg 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-1ATA_WDC_WD40EFRX-68N32N0_WD-WCC7K4PE4C1U -> ../../sdh 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-1ATA_WDC_WD40EFRX-68N32N0_WD-WCC7K7KKNSN9 -> ../../sdf 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-350014ee263ce2c81 -> ../../sdg 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-350014ee263e27e85 -> ../../sdh 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-350014ee263e2b396 -> ../../sdf 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-350014ee265d71fad -> ../../sde 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-355cd2e414f4a0b50 -> ../../sdc 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-355cd2e414f4a6b29 -> ../../sda 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-355cd2e414f4afc55 -> ../../sdd 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-355cd2e414f579528 -> ../../sdb 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-SATA_INTEL_SSDSCKKF12_BTLA810613SC128I -> ../../sdc 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-SATA_INTEL_SSDSCKKF12_BTLA810616PX128I -> ../../sdd 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-SATA_INTEL_SSDSCKKF12_BTLA81061ECP128I -> ../../sda 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-SATA_INTEL_SSDSCKKF12_BTLA81510DU3128I -> ../../sdb 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-SATA_WDC_WD40EFRX-68N_WD-WCC7K0CSZY00 -> ../../sde 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-SATA_WDC_WD40EFRX-68N_WD-WCC7K0RY7R37 -> ../../sdg 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-SATA_WDC_WD40EFRX-68N_WD-WCC7K4PE4C1U -> ../../sdh 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 scsi-SATA_WDC_WD40EFRX-68N_WD-WCC7K7KKNSN9 -> ../../sdf 
lrwxrwxrwx 1 root root  9 Aug  5 23:11 usb-Generic-_Compact_Flash_20060413092100000-0:0 -> ../../sdi 
lrwxrwxrwx 1 root root  9 Aug  5 23:11 usb-Generic-_MS_MS-Pro_20060413092100000-0:3 -> ../../sdl 
lrwxrwxrwx 1 root root  9 Aug  5 23:11 usb-Generic-_SD_MMC_20060413092100000-0:2 -> ../../sdk 
lrwxrwxrwx 1 root root  9 Aug  5 23:11 usb-Generic-_SM_xD-Picture_20060413092100000-0:1 -> ../../sdj 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 wwn-0x50014ee263ce2c81 -> ../../sdg 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 wwn-0x50014ee263e27e85 -> ../../sdh 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 wwn-0x50014ee263e2b396 -> ../../sdf 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 wwn-0x50014ee265d71fad -> ../../sde 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 wwn-0x55cd2e414f4a0b50 -> ../../sdc 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 wwn-0x55cd2e414f4a6b29 -> ../../sda 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 wwn-0x55cd2e414f4afc55 -> ../../sdd 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 wwn-0x55cd2e414f579528 -> ../../sdb
[/FONT]
```

---

