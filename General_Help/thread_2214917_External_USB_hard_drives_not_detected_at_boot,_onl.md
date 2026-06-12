---
title: "External USB hard drives not detected at boot, only when unplugging/reconnecting cabl"
date: 2014-04-03
forum: General Help
---

### Post by peterd2 on 2014-04-03
Any help appreciated. 
    
Using 13.10 with 3.13.7-031307-generic 


I have a 2 bay USB3 Vantec enclosure with 2x 3TB drives, both NTFS formatted (despite the mount point saying exfat it is ntfs, old name).  These are for storage, I do not boot off these drives.   The USB3 controller is a PCI-Express card that was added after linux was installed.

It all works fine if I unplug the USB cable and plug back in after booting, they mount per my fstab and work great until my next reboot.  

My fstab entries for the two drives


```
UUID=29984E231E14CE51 /mnt/WDEXFAT auto nosuid,nodev,nofail,x-gvfs-show,users,uid=1000,gid=1000,dmask=002,fmask=113,nobootwait 0 0


UUID=62C0D550C0D52AD5 /mnt/WDNTFS auto nosuid,nodev,nofail,x-gvfs-show,users,uid=1000,gid=1000,dmask=002,fmask=113,nobootwait 0 0

```

When I do a ```
lsusb
``` after a fresh reboot, my USB 3 controller does show up (along with other USB kb/mouse and such)


```
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

```

When I navigate to /etc/disk/* the drives are NOT listed on a fresh reboot in either id or uuid

When I do 

```
sudo modprobe usb-storage

```

Nothing is returned.  I've added usb-storage to /etc/modules as well in hopes of that getting it running at startup

When viewing ```
dmesg
```, I don't know what I'm looking for.  I don't see anything concerning USB 3, the enclosure or the drives there but there are a lot of entries and I'm a noob.

However, all of the following from dmesg when I unplug/reconnect the USB cable after booting up.  It looks like the enclosure (and therefor the drives) are not detected at all until I unplug the cable and plug it back in.  

```

[LIST=1]
[*][COLOR=#000000][  142.292121] usb 7-3: new high-speed USB device number 2 using xhci_hcd[/COLOR]
[*][COLOR=#000000][  142.312928] usb 7-3: New USB device found, idVendor=152d, idProduct=0551[/COLOR]
[*][COLOR=#000000][  142.312937] usb 7-3: New USB device strings: Mfr=1, Product=2, SerialNumber=5[/COLOR]
[*][COLOR=#000000][  142.312943] usb 7-3: Product: USB to ATA/ATAPI Bridge[/COLOR]
[*][COLOR=#000000][  142.312949] usb 7-3: Manufacturer: JMicron[/COLOR]
[*][COLOR=#000000][  142.312954] usb 7-3: SerialNumber: DC41281413FF[/COLOR]
[*][COLOR=#000000][  142.315086] usb-storage 7-3:1.0: USB Mass Storage device detected[/COLOR]
[*][COLOR=#000000][  142.315485] scsi6 : usb-storage 7-3:1.0[/COLOR]
[*][COLOR=#000000][  142.815052] usb 7-3: USB disconnect, device number 2[/COLOR]
[*][COLOR=#000000][  149.540115] usb 7-3: new high-speed USB device number 3 using xhci_hcd[/COLOR]
[*][COLOR=#000000][  149.540209] usb 7-3: Device not responding to set address.[/COLOR]
[*][COLOR=#000000][  149.744138] usb 7-3: Device not responding to set address.[/COLOR]
[*][COLOR=#000000][  149.948056] usb 7-3: device not accepting address 3, error -71[/COLOR]
[*][COLOR=#000000][  150.116322] usb 8-3: new SuperSpeed USB device number 2 using xhci_hcd[/COLOR]
[*][COLOR=#000000][  150.133493] usb 8-3: Parent hub missing LPM exit latency info.  Power management will be impacted.[/COLOR]
[*][COLOR=#000000][  150.135992] usb 8-3: New USB device found, idVendor=152d, idProduct=0551[/COLOR]
[*][COLOR=#000000][  150.135999] usb 8-3: New USB device strings: Mfr=1, Product=2, SerialNumber=5[/COLOR]
[*][COLOR=#000000][  150.136006] usb 8-3: Product: USB to ATA/ATAPI Bridge[/COLOR]
[*][COLOR=#000000][  150.136037] usb 8-3: Manufacturer: JMicron[/COLOR]
[*][COLOR=#000000][  150.136059] usb 8-3: SerialNumber: DC41281413FF[/COLOR]
[*][COLOR=#000000][  150.137695] usb-storage 8-3:1.0: USB Mass Storage device detected[/COLOR]
[*][COLOR=#000000][  150.138770] scsi7 : usb-storage 8-3:1.0[/COLOR]
[*][COLOR=#000000][  151.137781] scsi 7:0:0:0: Direct-Access     WDC WD30 EFRX-68EUZN0          PQ: 0 ANSI: 5[/COLOR]
[*][COLOR=#000000][  151.138238] scsi 7:0:0:1: Direct-Access     WDC WD30 EFRX-68EUZN0          PQ: 0 ANSI: 5[/COLOR]
[*][COLOR=#000000][  151.138926] sd 7:0:0:0: Attached scsi generic sg2 type 0[/COLOR]
[*][COLOR=#000000][  151.139290] sd 7:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).[/COLOR]
[*][COLOR=#000000][  151.139382] sd 7:0:0:1: Attached scsi generic sg3 type 0[/COLOR]
[*][COLOR=#000000][  151.139683] sd 7:0:0:0: [sdb] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)[/COLOR]
[*][COLOR=#000000][  151.139991] sd 7:0:0:1: [sdc] Very big device. Trying to use READ CAPACITY(16).[/COLOR]
[*][COLOR=#000000][  151.141063] sd 7:0:0:0: [sdb] Write Protect is off[/COLOR]
[*][COLOR=#000000][  151.141072] sd 7:0:0:0: [sdb] Mode Sense: 28 00 00 00[/COLOR]
[*][COLOR=#000000][  151.141359] sd 7:0:0:1: [sdc] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)[/COLOR]
[*][COLOR=#000000][  151.141797] sd 7:0:0:0: [sdb] No Caching mode page found[/COLOR]
[*][COLOR=#000000][  151.141915] sd 7:0:0:0: [sdb] Assuming drive cache: write through[/COLOR]
[*][COLOR=#000000][  151.143158] sd 7:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).[/COLOR]
[*][COLOR=#000000][  151.143996] sd 7:0:0:1: [sdc] Write Protect is off[/COLOR]
[*][COLOR=#000000][  151.144072] sd 7:0:0:1: [sdc] Mode Sense: 28 00 00 00[/COLOR]
[*][COLOR=#000000][  151.152206] sd 7:0:0:1: [sdc] No Caching mode page found[/COLOR]
[*][COLOR=#000000][  151.152368] sd 7:0:0:1: [sdc] Assuming drive cache: write through[/COLOR]
[*][COLOR=#000000][  151.152983] sd 7:0:0:0: [sdb] No Caching mode page found[/COLOR]
[*][COLOR=#000000][  151.153112] sd 7:0:0:0: [sdb] Assuming drive cache: write through[/COLOR]
[*][COLOR=#000000][  151.162254] sd 7:0:0:1: [sdc] Very big device. Trying to use READ CAPACITY(16).[/COLOR]
[*][COLOR=#000000][  151.194720] sd 7:0:0:1: [sdc] No Caching mode page found[/COLOR]
[*][COLOR=#000000][  151.194852] sd 7:0:0:1: [sdc] Assuming drive cache: write through[/COLOR]
[*][COLOR=#000000][  151.267875]  sdb: sdb1 sdb2[/COLOR]
[*][COLOR=#000000][  151.269517] sd 7:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).[/COLOR]
[*][COLOR=#000000][  151.279246] sd 7:0:0:0: [sdb] No Caching mode page found[/COLOR]
[*][COLOR=#000000][  151.279399] sd 7:0:0:0: [sdb] Assuming drive cache: write through[/COLOR]
[*][COLOR=#000000][  151.279547] sd 7:0:0:0: [sdb] Attached SCSI disk[/COLOR]
[*][COLOR=#000000][  151.280393]  sdc: sdc1 sdc2[/COLOR]
[*][COLOR=#000000][  151.282328] sd 7:0:0:1: [sdc] Very big device. Trying to use READ CAPACITY(16).[/COLOR]
[*][COLOR=#000000][  151.283720] sd 7:0:0:1: [sdc] No Caching mode page found[/COLOR]
[*][COLOR=#000000][  151.283842] sd 7:0:0:1: [sdc] Assuming drive cache: write through[/COLOR]
[*][COLOR=#000000][  151.283960] sd 7:0:0:1: [sdc] Attached SCSI disk[/COLOR]
[/LIST]

```

---

### Post by XBNCPRk on 2014-04-03
Unless Im mistaken your fstab is read only at startup. If theyre mounting when you unplug/replug them its automounting them because theyre a usb device.

---

