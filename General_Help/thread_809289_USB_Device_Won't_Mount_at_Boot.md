---
title: "USB Device Won't Mount at Boot"
date: 2008-05-27
forum: General Help
---

### Post by thecwin on 2008-05-27
As a horrible workaround, I've got a USB device set to mount as /boot and when I booted up the computer after the install, it entered maintenance mode. It failed to fsck.ext3, because it couldn't resolve the UUID of the volume. 

In /etc/fstab, I changed the last digit of the relevant line from 2 to 0, as to stop the fstab. The computer now boots, but it fails to mount /boot. It says the special device /dev/disk/by-uuid/c.... doesn't exist. If I perform **sudo mount -a** after startup, it successfully mounts /boot.

It seems that when Ubuntu tries to mount local drives, the USB devices aren't yet available, and it therefore fails to resolve UUIDs and mount drives. I've checked the UUIDs in /etc/fstab and if they correspond to the devices in /dev/disk/by-uuid, and it all seems to be correct. 

I checked dmesg and as you can see, this does appear to be the case:
> 
[   36.469431] usb usb3: configuration #1 chosen from 1 choice
[   36.469452] hub 3-0:1.0: USB hub found
[   36.469457] hub 3-0:1.0: 2 ports detected
[   36.493397] kjournald starting.  Commit interval 5 seconds
**[   36.493410] EXT3-fs: mounted filesystem with ordered data mode.** *(This is where it appears to be mounting local devices)*
[   36.579070] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 21
[   36.579083] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   36.579105] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   36.579130] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000d400
[   36.579228] usb usb4: configuration #1 chosen from 1 choice
[   36.579250] hub 4-0:1.0: USB hub found
......
[   41.614976] usbcore: registered new interface driver libusual
[   41.630073] Initializing USB Mass Storage driver...
[   41.632393] scsi5 : SCSI emulation for USB Mass Storage devices
[   41.633807] usbcore: registered new interface driver usb-storage
[   41.633816] USB Mass Storage support registered.
[   41.633942] usb-storage: device found at 2
[   41.633944] usb-storage: waiting for device to settle before scanning
[   43.643406] loop: module loaded
[   43.680645] lp: driver loaded but no devices found
[   43.916791] Adding 2795268k swap on /dev/sda5.  Priority:-1 extents:1 across:2795268k
[   44.272851] EXT3 FS on sda1, internal journal
[   44.977840] ip_tables: (C) 2000-2006 Netfilter Core Team
[   46.080186] NET: Registered protocol family 10
[   46.080379] lo: Disabled Privacy Extensions
[   46.623615] usb-storage: device scan complete
**[   46.627964] scsi 5:0:0:0: Direct-Access     WD       2500BB External  0412 PQ: 0 ANSI: 0** *(But it only seems to detect the USB device down here...)*
[   46.641211] sd 5:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)


My /etc/fstab is as follows
> 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a54b32c5-4d66-4643-8176-02ff61adc86e /               ext3    noatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=c53092fc-3d24-46c8-ba7b-cd0c835d1d08 /boot           ext3    noatime         0       0

# /dev/sda5
UUID=c95c9c12-b84b-4018-8cad-b40b0482b75d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Just checking the UUID:
> 
**cameron@media01:~$** ls -lh /dev/disk/by-uuid/c53092fc-3d24-46c8-ba7b-cd0c835d1d08 
lrwxrwxrwx 1 root root 10 2008-05-27 14:14 /dev/disk/by-uuid/c53092fc-3d24-46c8-ba7b-cd0c835d1d08 -> ../../sdb1




Thanks :)

---

### Post by ibuclaw on 2008-05-27
You can change the order of which the initramfs loads the modules, at least I think you should be able to.

```
gedit /etc/initramfs-tools/initramfs.conf
```

By default, the assignment is:
```
MODULES=most
```
Though you could try:
```
MODULES=dep
```
To see if that will make a difference.

Then make a backup of your current initrd file
```
sudo cp /boot/initrd.img-**<kernel number>** /boot/initrd.img-**<kernel number>**.my.backup
```

Then
```
sudo dpkg-reconfigure linux-image**<kernel number>**
```
to rebuild the module list.

Regards
Iain

---

### Post by ibuclaw on 2008-05-27
Alternately, if you feel really úber-core.

You can set
```
MODULES=list
```
And open up the modules file
```
gedit /etc/initramfs-tools/modules
```
And manually put in the order that you want to modules to load there.
ie:
```

scsi_mod
sd_mod
libata
ata_piix
raid1
md
ext3

```

To get the full list of modules you currently have, run this semi-oneliner (vor if your reading this... don't laugh :) )
```
for i in `find /sys/ -name modalias -exec cat {} \; 2>/dev/null`; do /sbin/modprobe --config /dev/null --show-depends $i 2>/dev/null; done | rev | cut -f 1 -d '/' | rev | sort -u
```

And you'll just have to figure out which ones are for all your filesystems. (Should be pretty easy).

Regards
Iain

---

