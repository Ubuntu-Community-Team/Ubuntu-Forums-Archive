---
title: "Mounting external harddrives fails"
date: 2007-10-25
forum: General Help
---

### Post by joneZ on 2007-10-25
Hi,

I have just installed Gutsy on my laptop, though had feisty and edgy and dapper before but I 
always upgraded. But I wanne to try out how easy it to install Gutsy ( thx to the devs ).

But now I have a strange problem ... Gnome doesn't automount the harddrives like before. It gives the error message "**Can't mount the volume** Invalid option the to mount the volume "ERIK". 

Filesystem on this partion is vfat32

Here is a syslog snippets. 
```

Oct 25 13:57:17 siXel kernel: [  400.312000] usb 1-7: new high speed USB device using ehci_hcd and address 9
Oct 25 13:57:18 siXel kernel: [  400.444000] usb 1-7: configuration #1 chosen from 1 choice
Oct 25 13:57:18 siXel kernel: [  400.444000] scsi3 : SCSI emulation for USB Mass Storage devices
Oct 25 13:57:18 siXel kernel: [  400.444000] usb-storage: device found at 9
Oct 25 13:57:18 siXel kernel: [  400.444000] usb-storage: waiting for device to settle before scanning
Oct 25 13:57:18 siXel NetworkManager: <debug> [1193313438.097827] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_702_noserial'). 
Oct 25 13:57:18 siXel NetworkManager: <debug> [1193313438.191861] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_702_noserial_if0'). 
Oct 25 13:57:18 siXel NetworkManager: <debug> [1193313438.195812] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_702_noserial_usbraw'). 
Oct 25 13:57:23 siXel kernel: [  405.444000] usb-storage: device scan complete
Oct 25 13:57:23 siXel kernel: [  405.648000] scsi 3:0:0:0: Direct-Access     ST94011A                  0811 PQ: 0 ANSI: 0
Oct 25 13:57:23 siXel kernel: [  405.652000] sd 3:0:0:0: [sdb] 78140160 512-byte hardware sectors (40008 MB)
Oct 25 13:57:23 siXel kernel: [  405.652000] sd 3:0:0:0: [sdb] Test WP failed, assume Write Enabled
Oct 25 13:57:23 siXel kernel: [  405.652000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
Oct 25 13:57:23 siXel kernel: [  405.656000] sd 3:0:0:0: [sdb] 78140160 512-byte hardware sectors (40008 MB)
Oct 25 13:57:23 siXel kernel: [  405.656000] sd 3:0:0:0: [sdb] Test WP failed, assume Write Enabled
Oct 25 13:57:23 siXel kernel: [  405.656000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
Oct 25 13:57:23 siXel kernel: [  405.656000]  sdb: sdb1
Oct 25 13:57:23 siXel kernel: [  405.676000] sd 3:0:0:0: [sdb] Attached SCSI disk
Oct 25 13:57:23 siXel kernel: [  405.676000] sd 3:0:0:0: Attached scsi generic sg1 type 0
Oct 25 13:57:23 siXel NetworkManager: <debug> [1193313443.574846] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_702_noserial_if0_scsi_host'). 
Oct 25 13:57:23 siXel NetworkManager: <debug> [1193313443.577540] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_702_noserial_if0_scsi_host_scsi_device_lun0'). 
Oct 25 13:57:23 siXel NetworkManager: <debug> [1193313443.579002] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_702_noserial_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 25 13:57:23 siXel NetworkManager: <debug> [1193313443.642857] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_ST94011A_USB_TO_IDE_0_0'). 
Oct 25 13:57:23 siXel NetworkManager: <debug> [1193313443.703857] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_00B2_3DE2'). 
Oct 25 13:57:23 siXel kernel: [  406.260000] UDF-fs: No VRS found
Oct 25 13:57:23 siXel kernel: [  406.308000] Unable to identify CD-ROM format.

```

If I switch to the console and type "mount /dev/sdb1 /mnt" it works like a charme. But it definitly worked in feisty with this harddrives.

I assume I missing some packages, but wich ...

Someone has a glue.

Greetings
Erik

---

### Post by joneZ on 2007-10-25
Some more information 


This is caused by pmount ... ( I'm in the group plugdev )

If I do

```
mount /dev/sdb1 /mnt 
```

it works like a charme

If I do

```
pmount /dev/sdb1  
```

it should mount under /media/<LABEL> or /media/<device> as it says in the manpage, but
in syslog and dmesg I see


```
[ 7407.720000] UDF-fs: No VRS found
[ 7407.788000] Unable to identify CD-ROM format.
```


It doesn't matter if it is root or another user. 

Anyone else having this problem ?? 

Greetings
Erik

---

### Post by joneZ on 2007-10-25
I saw on the web that pmount needs a helper application like gnome-volume-manager, wich is 
installed and running, according to ps aux:

I know have try to digged into that a little bit more ... It doesn't depend on the FS-Type 

It always says: 

[ 1790.820000] UDF-fs: No VRS found
[ 1790.864000] Unable to identify CD-ROM format.

at the end of each plug in of an external drive/stick whatever. I have tested this with ntfs/vfat/ext3/ext2 


Any hints 
Erik

---

### Post by joneZ on 2007-10-25
this all was caused by an entry in the /etc/fstab 

/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Explanation: 

I had feisty before and downloaded gutsy and converted the iso image with isotostick.sh ( found at 
planet.ubuntu.com), because I have a Dell D430 wich has no cd-drive. My docking station and cd-drive are at work so I decided to boot via USB-Stick.

I assume this line was added automatic during install. and the later causes the problem, because every time I plug in the a drive it get's  mount to /media/cdrom0 wich had no udf nor iso9660. 


Greetings
Erik

---

### Post by korel31 on 2007-11-09
I just got done installing Gutsy on my dell x300 from a USB drive. Install went fine but afterwards I experienced the same problem, it refused to mount the same USB drive it was installed from. Indeed pmount always throw the no VRS found but mount works perfectly.

---

