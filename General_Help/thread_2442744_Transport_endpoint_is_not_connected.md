---
title: "Transport endpoint is not connected"
date: 2020-05-07
forum: General Help
---

### Post by joaompr on 2020-05-07
Hello all, 
When a connect this external HDD to my Ubuntu 20.04 I get this error: "...*Transport endpoint* is *not connected* " I guess this can be caused by something with disk, file system damaged or other situations. I can use the sane HDD in a Window box and another box with Fedora (I'm using it in this moment). 
Below is **dmesg** output , first from Ubuntu , them from Fedora, what can I do to have this HDD working in Ubuntu? 

Thanks for you help. 

```

Ubuntu 20.04  
 
[ 3319.320821] ---[ end trace a5078a3f5b07dc75 ]--- 
[ 3615.362802] usb 1-1.1: new high-speed USB device number 5 using ehci-pci 
[ 3615.392239] usb 1-1.1: New USB device found, idVendor=17ef, idProduct=4532, bcdDevice= 1.19 
[ 3615.392246] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3 
[ 3615.392250] usb 1-1.1: Product: Secure 1TB  3.0 
[ 3615.392253] usb 1-1.1: Manufacturer: ThinkPad 
[ 3615.392257] usb 1-1.1: SerialNumber: 333353374650525153202020 
[ 3615.392826] usb-storage 1-1.1:1.0: USB Mass Storage device detected 
[ 3615.397356] scsi host2: usb-storage 1-1.1:1.0 
[ 3616.427976] scsi 2:0:0:0: Direct-Access     ThinkPad Secure 1TB  3.0  0119 PQ: 0 ANSI: 6 
[ 3616.428621] sd 2:0:0:0: Attached scsi generic sg2 type 0 
[ 3616.435263] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/932 GiB) 
[ 3616.438054] sd 2:0:0:0: [sdb] Write Protect is off 
[ 3616.438062] sd 2:0:0:0: [sdb] Mode Sense: 2b 00 10 08 
[ 3616.441320] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, supports DPO and FUA 
[ 3616.583558]  sdb: sdb1 
[ 3616.587376] sd 2:0:0:0: [sdb] Attached SCSI disk 
[ 3616.949454] UDF-fs: warning (device sdb): udf_load_vrs: No VRS found 
[ 3616.949463] UDF-fs: Scanning with blocksize 512 failed 
[ 3616.949925] UDF-fs: warning (device sdb): udf_load_vrs: No VRS found 
[ 3616.949927] UDF-fs: Scanning with blocksize 1024 failed 
[ 3616.950398] UDF-fs: warning (device sdb): udf_load_vrs: No VRS found 
[ 3616.950400] UDF-fs: Scanning with blocksize 2048 failed 
[ 3616.950775] UDF-fs: warning (device sdb): udf_load_vrs: No VRS found 
[ 3616.950776] UDF-fs: Scanning with blocksize 4096 failed 
[ 3616.995271] ISOFS: Unable to identify CD-ROM format. 
[ 3617.001501] FAT-fs (sdb): invalid media value (0xf3) 
[ 3617.001513] FAT-fs (sdb): Can't find a valid FAT filesystem 
[ 3617.008164] hfsplus: unable to find HFS+ superblock 
[ 3617.013289] hfs: can't find a HFS filesystem on dev sdb 
[ 3617.017796] EXT4-fs (sdb): VFS: Can't find ext4 filesystem 
[ 3617.022263] EXT4-fs (sdb): VFS: Can't find ext4 filesystem 
[ 3617.026509] EXT4-fs (sdb): VFS: Can't find ext4 filesystem 
[ 3617.031646] REISERFS warning (device sdb): sh-2021 reiserfs_fill_super: can not find reiserfs on sdb 
[ 3617.052740] XFS (sdb): Invalid superblock magic number 
[ 3617.063166] omfs: Invalid superblock (66556653) 
 
 
Fedora 32 
[38208.534139] usb 2-2: new SuperSpeed Gen 1 USB device number 3 using xhci_hcd 
[38208.546886] usb 2-2: New USB device found, idVendor=17ef, idProduct=4532, bcdDevice= 1.19 
[38208.546889] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3 
[38208.546891] usb 2-2: Product: Secure 1TB  3.0 
[38208.546892] usb 2-2: Manufacturer: ThinkPad 
[38208.546894] usb 2-2: SerialNumber: 333353374650525153202020 
[38208.551839] usb-storage 2-2:1.0: USB Mass Storage device detected 
[38208.552182] scsi host2: usb-storage 2-2:1.0 
[38209.576904] scsi 2:0:0:0: Direct-Access     ThinkPad Secure 1TB  3.0  0119 PQ: 0 ANSI: 6 
[38209.577356] sd 2:0:0:0: Attached scsi generic sg2 type 0 
[38209.577588] sd 2:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/932 GiB) 
[38209.577804] sd 2:0:0:0: [sdc] Write Protect is off 
[38209.577808] sd 2:0:0:0: [sdc] Mode Sense: 2b 00 10 08 
[38209.578061] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, supports DPO and FUA 
[38209.694950]  sdc: sdc1 
[38209.696138] sd 2:0:0:0: [sdc] Attached SCSI disk 
[38755.527919] usb 2-2: USB disconnect, device number 3 
[38755.534052] sd 2:0:0:0: [sdc] Synchronizing SCSI cache 
[38755.534113] sd 2:0:0:0: [sdc] Synchronize Cache(10) failed: Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK 
[38894.369797] usb 2-2: new SuperSpeed Gen 1 USB device number 4 using xhci_hcd 
[38894.382471] usb 2-2: New USB device found, idVendor=17ef, idProduct=4532, bcdDevice= 1.19 
[38894.382473] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3 
[38894.382476] usb 2-2: Product: Secure 1TB  3.0 
[38894.382477] usb 2-2: Manufacturer: ThinkPad 
[38894.382478] usb 2-2: SerialNumber: 333353374650525153202020 
[38894.386832] usb-storage 2-2:1.0: USB Mass Storage device detected 
[38894.387086] scsi host2: usb-storage 2-2:1.0 
[38895.400358] scsi 2:0:0:0: Direct-Access     ThinkPad Secure 1TB  3.0  0119 PQ: 0 ANSI: 6 
[38895.400717] sd 2:0:0:0: Attached scsi generic sg2 type 0 
[38895.400948] sd 2:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/932 GiB) 
[38895.401164] sd 2:0:0:0: [sdc] Write Protect is off 
[38895.401168] sd 2:0:0:0: [sdc] Mode Sense: 2b 00 10 08 
[38895.401387] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, supports DPO and FUA 
[38895.511469]  sdc: sdc1 
[38895.512785] sd 2:0:0:0: [sdc] Attached SCSI disk

```

---

### Post by cariboo on 2020-05-07
Moved to General Help, as Focal has been released.

---

