---
title: "Fiesty Does Not Recognize GSA-E40L (LG DVD Burner)"
date: 2008-03-15
forum: General Help
---

### Post by Aktrop on 2008-03-15
I have a an external DVD burner connected by USB to my laptop, and Feisty just does not recognize it. It's a LG DVD burner (GSA-E40L). The output of 

sudo lshw -C disk 

is:

```

 *-disk                  
       description: SCSI Disk
       product: HTS548040M9AT00
       vendor: ATA
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: MG2O
       serial: MRL202L2HZXV0B
       size: 37GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          capacity: 1098MB
          capabilities: primary
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: scsi@0:0.0.0,2
          logical name: /dev/sda2
          size: 1474MB
          capacity: 1474MB
          capabilities: primary extended partitioned partitioned:extended
        *-logicalvolume
             description: Linux swap / Solaris partition
             physical id: 5
             logical name: /dev/sda5
             capacity: 1474MB
             capabilities: nofs
     *-volume:2
          description: Linux filesystem partition
          physical id: 3
          bus info: scsi@0:0.0.0,3
          logical name: /dev/sda3
          capacity: 34GB
          capabilities: primary
  *-cdrom
       description: DVD reader
       product: DVD-ROM SD-R9012
       vendor: TOSHIBA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1121
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5
     *-disc
          physical id: 0
          logical name: /dev/cdrom


```

Any help would be great! Thanks!

---

### Post by Aktrop on 2008-03-18
(BUMP)

Anybody out there?

---

