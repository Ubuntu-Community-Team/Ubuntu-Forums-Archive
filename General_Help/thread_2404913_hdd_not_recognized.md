---
title: "hdd not recognized"
date: 2018-10-30
forum: General Help
---

### Post by stefania010101010101 on 2018-10-30
hi,
 I-m tring to read a wd my cloud that not work. I connected by usb to my  computer but fdisk not see this hdd. I used sudo lshw and i see this
*-usb:3
                   description: Mass storage device
                   product: ASM1153E
                   vendor: asmedia
                   physical id: 6
                   bus info: usb@3:6
                   logical name: scsi7
                   version: 1.00
                   serial: 0123456789012
                   capabilities: usb-2.10 scsi
                   configuration: driver=uas speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: ASM1153E
                      vendor: asmedia
                      physical id: 0.0.0
                      bus info: scsi@7:0.0.0
                      logical name: /dev/sdb
                      version: 0
                      serial: 2109876543210
                      configuration: ansiversion=6 logicalsectorsize=512 sectors

how i can open and recover files from this device?

---

### Post by lordboltar on 2018-10-30
Is the USB port 2.0 or 3.0 makes a difference on the drive if your drive is 3 and your machine is 2 

have a look here for data recovery

[https://www.r-studio.com/data_recovery_linux/](https://www.r-studio.com/data_recovery_linux/)

---

