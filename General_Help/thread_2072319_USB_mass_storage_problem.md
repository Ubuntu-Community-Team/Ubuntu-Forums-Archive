---
title: "USB mass storage problem"
date: 2012-10-17
forum: General Help
---

### Post by jeffpkamp on 2012-10-17
I am running Ubuntu 12.04 lts.  I am trying to use my usb cable to move files from my computer to my phone (samsung eternity II).  Normally it loads up a drive when I plug it in.  it doesn't seem to be mounting though.  dmesg after plugging in gives:

 
[ 7783.821085] usb 1-1.4: new high-speed USB device number 11 using ehci_hcd
[ 7783.917935] scsi11 : usb-storage 1-1.4:1.0
[ 7784.917773] scsi 11:0:0:0: Direct-Access     SAMSUNG  MMC Storage      2.31 PQ: 0 ANSI: 2
[ 7784.919218] sd 11:0:0:0: Attached scsi generic sg3 type 0
[ 7784.920532] sd 11:0:0:0: [sdc] 7733248 512-byte logical blocks: (3.95 GB/3.68 GiB)
[ 7784.921307] sd 11:0:0:0: [sdc] Write Protect is off
[ 7784.921318] sd 11:0:0:0: [sdc] Mode Sense: 0f 0e 00 00
[ 7784.921928] sd 11:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 7784.929748]  sdc: sdc1
[ 7784.934756] sd 11:0:0:0: [sdc] Attached SCSI removable disk
[ 7785.006227] sd 11:0:0:0: [sdc] Synchronizing SCSI cache

so the computer see's it and this is similar to what i see when I plug in a USB drive, minus that last message about synchronizing.  

lsusb gives:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 1d57:0008  
Bus 001 Device 009: ID 0781:5530 SanDisk Corp. Cruzer
Bus 002 Device 003: ID 04f2:b130 Chicony Electronics Co., Ltd 
Bus 002 Device 005: ID 0930:020f Toshiba Corp. 
Bus 001 Device 011: ID 04e8:f000 Samsung Electronics Co., Ltd 

My phone would be that last one there.  So I'm not sure why its not mounting or even showing up as a device. fdisk -l only shows sda and sdb, no sdc (which is what it says it loads as.  Kind of confused, so any help is appreciated.

---

### Post by jeffpkamp on 2012-10-17
So I solved this one a whole two seconds after posting this, but I would like some input as to why this keeps happening.  To fix it I went to lsmod, found a module called usb_storage, and used rmmod -> modprobe to remove and reload the module.  Then I plugged in my jumpdrive, and the computer detected both the jumpdrive and my phone drive and mounted them...

I am noticing that removing and reloading modules is a common way to make things work in ubuntu, I am just wondering why, and if it is something that I am doing that is causing this.

---

