---
title: "USB disk keep disconnecting"
date: 2022-01-31
forum: General Help
---

### Post by georgesgiralt on 2022-01-31
Hello all ! 
I have a very recent laptop from Lenovo. Thinkbook 15G2 ITL. On it I I've installed Ubuntu 20.04.3 LTS and keep it current with all updates applied. 
I use a no name USB 2.0  adapter to plug a Seagate FireCuda 2TO 2.5" disk I use to make backup and a copy of my Ubuntu installation. It works well but is awfully slow. 
I've bought an  ICY BOX IB-AC704-6G USB 3.0 to SATA interface for the same use which I expect to be faster. 
Alas, the disk keep disappearing and reconnecting making backups impossible.  
See :
```

[40329.185888] usb 4-2: new SuperSpeed USB device number 13 using xhci_hcd
[40329.206536] usb 4-2: New USB device found, idVendor=174c, idProduct=55aa, bcdDevice= 1.00
[40329.206546] usb 4-2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[40329.206549] usb 4-2: Product: IB-AC704-6G
[40329.206552] usb 4-2: Manufacturer: ICY BOX
[40329.206555] usb 4-2: SerialNumber: 2017120001C3
[40329.208417] usb-storage 4-2:1.0: USB Mass Storage device detected
[40329.208735] usb-storage 4-2:1.0: Quirks match for vid 174c pid 55aa: 400000
[40329.210291] scsi host3: usb-storage 4-2:1.0
[40330.232087] scsi 3:0:0:0: Direct-Access     ICY BOX  IB-AC704-6G      0    PQ: 0 ANSI: 6
[40330.232658] sd 3:0:0:0: Attached scsi generic sg4 type 0
[40330.232848] sd 3:0:0:0: [sdd] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[40330.233135] sd 3:0:0:0: [sdd] Write Protect is off
[40330.233138] sd 3:0:0:0: [sdd] Mode Sense: 43 00 00 00
[40330.233422] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[40330.300151]  sdd: sdd1 sdd2 sdd3 sdd4 sdd5
[40330.328251] sd 3:0:0:0: [sdd] Attached SCSI disk
[40469.742395] usb 4-2: USB disconnect, device number 13
[40469.747948] sd 3:0:0:0: [sdd] Synchronizing SCSI cache
[40469.747982] sd 3:0:0:0: [sdd] Synchronize Cache(10) failed: Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[40470.086466] usb 4-2: new SuperSpeed USB device number 14 using xhci_hcd
[40470.107254] usb 4-2: New USB device found, idVendor=174c, idProduct=55aa, bcdDevice= 1.00
[40470.107265] usb 4-2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[40470.107269] usb 4-2: Product: IB-AC704-6G
[40470.107272] usb 4-2: Manufacturer: ICY BOX
[40470.107274] usb 4-2: SerialNumber: 2017120001C3
[40470.109180] usb-storage 4-2:1.0: USB Mass Storage device detected
[40470.109443] usb-storage 4-2:1.0: Quirks match for vid 174c pid 55aa: 400000
[40470.109597] scsi host3: usb-storage 4-2:1.0
[40471.126958] scsi 3:0:0:0: Direct-Access     ICY BOX  IB-AC704-6G      0    PQ: 0 ANSI: 6
[40471.127460] sd 3:0:0:0: Attached scsi generic sg4 type 0
[40471.127948] sd 3:0:0:0: [sdd] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[40471.128411] sd 3:0:0:0: [sdd] Write Protect is off
[40471.128418] sd 3:0:0:0: [sdd] Mode Sense: 43 00 00 00
[40471.128792] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[40471.187927]  sdd: sdd1 sdd2 sdd3 sdd4 sdd5
[40471.204602] sd 3:0:0:0: [sdd] Attached SCSI disk
[40647.227155] usb 4-2: USB disconnect, device number 14
[40647.231981] sd 3:0:0:0: [sdd] Synchronizing SCSI cache
[40647.232005] sd 3:0:0:0: [sdd] Synchronize Cache(10) failed: Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[40647.583235] usb 4-2: new SuperSpeed USB device number 15 using xhci_hcd
[40647.603892] usb 4-2: New USB device found, idVendor=174c, idProduct=55aa, bcdDevice= 1.00
[40647.603903] usb 4-2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[40647.603907] usb 4-2: Product: IB-AC704-6G
[40647.603910] usb 4-2: Manufacturer: ICY BOX
[40647.603913] usb 4-2: SerialNumber: 2017120001C3
[40647.606171] usb-storage 4-2:1.0: USB Mass Storage device detected
[40647.606487] usb-storage 4-2:1.0: Quirks match for vid 174c pid 55aa: 400000
[40647.606576] scsi host3: usb-storage 4-2:1.0
[40648.631803] scsi 3:0:0:0: Direct-Access     ICY BOX  IB-AC704-6G      0    PQ: 0 ANSI: 6
[40648.632349] sd 3:0:0:0: Attached scsi generic sg4 type 0
[40648.632804] sd 3:0:0:0: [sdd] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[40648.633102] sd 3:0:0:0: [sdd] Write Protect is off
[40648.633108] sd 3:0:0:0: [sdd] Mode Sense: 43 00 00 00
[40648.633402] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[40648.693686]  sdd: sdd1 sdd2 sdd3 sdd4 sdd5
[40648.713788] sd 3:0:0:0: [sdd] Attached SCSI disk
[41676.648674] usb 4-2: USB disconnect, device number 15
[41676.656972] sd 3:0:0:0: [sdd] Synchronizing SCSI cache
[41676.657004] sd 3:0:0:0: [sdd] Synchronize Cache(10) failed: Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[41677.000791] usb 4-2: new SuperSpeed USB device number 16 using xhci_hcd
[41677.021549] usb 4-2: New USB device found, idVendor=174c, idProduct=55aa, bcdDevice= 1.00
[41677.021559] usb 4-2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[41677.021562] usb 4-2: Product: IB-AC704-6G
[41677.021565] usb 4-2: Manufacturer: ICY BOX
[41677.021567] usb 4-2: SerialNumber: 2017120001C3
[41677.023834] usb-storage 4-2:1.0: USB Mass Storage device detected
[41677.024117] usb-storage 4-2:1.0: Quirks match for vid 174c pid 55aa: 400000
[41677.024254] scsi host3: usb-storage 4-2:1.0
[41678.045365] scsi 3:0:0:0: Direct-Access     ICY BOX  IB-AC704-6G      0    PQ: 0 ANSI: 6
[41678.045769] sd 3:0:0:0: Attached scsi generic sg4 type 0
[41678.046238] sd 3:0:0:0: [sdd] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[41678.046534] sd 3:0:0:0: [sdd] Write Protect is off
[41678.046537] sd 3:0:0:0: [sdd] Mode Sense: 43 00 00 00
[41678.046823] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[41678.110278]  sdd: sdd1 sdd2 sdd3 sdd4 sdd5
[41678.139291] sd 3:0:0:0: [sdd] Attached SCSI disk
[41849.469630] usb 4-2: USB disconnect, device number 16
[41849.476416] sd 3:0:0:0: [sdd] Synchronizing SCSI cache
[41849.476449] sd 3:0:0:0: [sdd] Synchronize Cache(10) failed: Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[41849.817584] usb 4-2: new SuperSpeed USB device number 17 using xhci_hcd
[41849.838431] usb 4-2: New USB device found, idVendor=174c, idProduct=55aa, bcdDevice= 1.00
[41849.838441] usb 4-2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[41849.838444] usb 4-2: Product: IB-AC704-6G
[41849.838447] usb 4-2: Manufacturer: ICY BOX
[41849.838449] usb 4-2: SerialNumber: 2017120001C3
[41849.840341] usb-storage 4-2:1.0: USB Mass Storage device detected
[41849.840646] usb-storage 4-2:1.0: Quirks match for vid 174c pid 55aa: 400000
[41849.840753] scsi host3: usb-storage 4-2:1.0
[41850.846290] scsi 3:0:0:0: Direct-Access     ICY BOX  IB-AC704-6G      0    PQ: 0 ANSI: 6
[41850.846848] sd 3:0:0:0: Attached scsi generic sg4 type 0
[41850.847123] sd 3:0:0:0: [sdd] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[41850.847414] sd 3:0:0:0: [sdd] Write Protect is off
[41850.847419] sd 3:0:0:0: [sdd] Mode Sense: 43 00 00 00
[41850.847704] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[41850.939026]  sdd: sdd1 sdd2 sdd3 sdd4 sdd5
[41850.960252] sd 3:0:0:0: [sdd] Attached SCSI disk

```
The gizmo use an 
```
ID 174c:55aa ASMedia Technology Inc. Name: ASM1051E SATA 6Gb/s bridge, ASM1053E SATA 6Gb/s bridge, ASM1153 SATA 3Gb/s bridge, ASM1153E SATA 6Gb/s bridge
```
I already have a similar interface in my Blue Ray external drive and it runs flawlessly for hours. 
So I attempted to find where the fault lies. 
I first tried to plug a smaller disk (500 Go Western Digital,2.5" size.) no luck. 
Then I plugged either disks to a Thunderbolt hub I have with a 65 W power supply.  No joy either. 
This device has a plug for a 12V power supply when you want to use it for 3.5 " disks. So I plugged the 12 V and a 3.5" 320 GB Seagate disk. No luck either. 
In syslog I get a little more detailed information :
```

espineux kernel: [42959.842961] usb 4-2: new SuperSpeed USB device number 26 using xhci_hcd
Jan 31 16:12:21  kernel: [42959.863621] usb 4-2: New USB device found, idVendor=174c, idProduct=55aa, bcdDevice= 1.00
Jan 31 16:12:21  kernel: [42959.863630] usb 4-2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
Jan 31 16:12:21  kernel: [42959.863634] usb 4-2: Product: IB-AC704-6G
Jan 31 16:12:21  kernel: [42959.863636] usb 4-2: Manufacturer: ICY BOX
Jan 31 16:12:21  kernel: [42959.863638] usb 4-2: SerialNumber: 2017120001C3
Jan 31 16:12:21  kernel: [42959.865502] usb-storage 4-2:1.0: USB Mass Storage device detected
Jan 31 16:12:21  kernel: [42959.865882] usb-storage 4-2:1.0: Quirks match for vid 174c pid 55aa: 400000
Jan 31 16:12:21  kernel: [42959.865985] scsi host3: usb-storage 4-2:1.0
Jan 31 16:12:21  mtp-probe: checking bus 4, device 26: "/sys/devices/pci0000:00/0000:00:14.0/usb4/4-2"
Jan 31 16:12:21  mtp-probe: bus: 4, device: 26 was not an MTP device
Jan 31 16:12:22  kernel: [42960.370946] usb 4-2: USB disconnect, device number 26
Jan 31 16:12:22  kernel: [42960.655008] usb 4-2: new SuperSpeed USB device number 27 using xhci_hcd
Jan 31 16:12:22  kernel: [42960.679442] usb 4-2: New USB device found, idVendor=174c, idProduct=55aa, bcdDevice= 1.00
Jan 31 16:12:22  kernel: [42960.679453] usb 4-2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
Jan 31 16:12:22  kernel: [42960.679457] usb 4-2: Product: IB-AC704-6G
Jan 31 16:12:22  kernel: [42960.679461] usb 4-2: Manufacturer: ICY BOX
Jan 31 16:12:22  kernel: [42960.679464] usb 4-2: SerialNumber: 2017120001C3
Jan 31 16:12:22  kernel: [42960.681215] usb-storage 4-2:1.0: USB Mass Storage device detected
Jan 31 16:12:22  kernel: [42960.681532] usb-storage 4-2:1.0: Quirks match for vid 174c pid 55aa: 400000
Jan 31 16:12:22  kernel: [42960.681646] scsi host3: usb-storage 4-2:1.0
Jan 31 16:12:22  mtp-probe: checking bus 4, device 27: "/sys/devices/pci0000:00/0000:00:14.0/usb4/4-2"
Jan 31 16:12:22  mtp-probe: bus: 4, device: 27 was not an MTP device
Jan 31 16:12:22  mtp-probe: checking bus 4, device 27: "/sys/devices/pci0000:00/0000:00:14.0/usb4/4-2"
Jan 31 16:12:22  mtp-probe: bus: 4, device: 27 was not an MTP device
Jan 31 16:12:23  mtp-probe: checking bus 4, device 27: "/sys/devices/pci0000:00/0000:00:14.0/usb4/4-2"
Jan 31 16:12:23  mtp-probe: bus: 4, device: 27 was not an MTP device
Jan 31 16:12:23  kernel: [42961.699279] scsi 3:0:0:0: Direct-Access     ICY BOX  IB-AC704-6G      0    PQ: 0 ANSI: 6
Jan 31 16:12:23  kernel: [42961.699689] sd 3:0:0:0: Attached scsi generic sg4 type 0
Jan 31 16:12:23  kernel: [42961.699873] sd 3:0:0:0: [sdd] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Jan 31 16:12:23  kernel: [42961.700180] sd 3:0:0:0: [sdd] Write Protect is off
Jan 31 16:12:23  kernel: [42961.700188] sd 3:0:0:0: [sdd] Mode Sense: 43 00 00 00
Jan 31 16:12:23  kernel: [42961.700471] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 31 16:12:24  kernel: [42961.906445]  sdd: sdd1 sdd2 sdd3 sdd4 sdd5
Jan 31 16:12:24  kernel: [42961.941700] sd 3:0:0:0: [sdd] Attached SCSI disk
Jan 31 16:12:25  ntfs-3g[53440]: Version 2017.3.23AR.3 integrated FUSE 28
Jan 31 16:12:25  ntfs-3g[53440]: Mounted /dev/sdd4 (Read-Write, label "Windows10", NTFS 3.1)
Jan 31 16:12:25  ntfs-3g[53440]: Cmdline options: rw,nodev,nosuid,windows_names,uid=1000,gid=1000,uhelper=udisks2
Jan 31 16:12:25  ntfs-3g[53440]: Mount options: nodev,nosuid,uhelper=udisks2,allow_other,nonempty,relatime,rw,default_permissions,fsname=/dev/sdd4,blkdev,blksize=4096
Jan 31 16:12:25  ntfs-3g[53440]: Global ownership and permissions enforced, configuration type 7
Jan 31 16:12:25  systemd[1]: Finished Clean the /media/georges/Windows10 mount point.
Jan 31 16:12:25  udisksd[1222]: Mounted /dev/sdd4 at /media/georges/Windows10 on behalf of uid 1000
Jan 31 16:12:25  dbus-daemon[3037]: [session uid=1000 pid=3037] Activating service name='org.gnome.Shell.HotplugSniffer' requested by ':1.46' (uid=1000 pid=3314 comm="/usr/bin/gnome-shell " label="unconfined")
Jan 31 16:12:25  dbus-daemon[3037]: [session uid=1000 pid=3037] Successfully activated service 'org.gnome.Shell.HotplugSniffer'
Jan 31 16:12:25  ntfs-3g[53440]: Could not load plugin /usr/lib/x86_64-linux-gnu/ntfs-3g/ntfs-plugin-80000017.so: Succès
Jan 31 16:12:25  ntfs-3g[53440]: Hint /usr/lib/x86_64-linux-gnu/ntfs-3g/ntfs-plugin-80000017.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type

```
At first, I though I had a problem with Fuse NTFS support but the missing library is for compressed files on NTFS volumes which I couldn't care less. And I tried with a disk without NTFS partition with no joy either. 
I've found that I may have a problem with UAS module as this chip need/use uasp. But the uas module gets loaded and seems to be used :
```

 lsmod | grep uas
uas                    28672  0
usb_storage            73728  3 uas
```
And the USB subsystem report  fine :
```

lsusb -v -d 174c:55aa | grep -i interface
can't get debug descriptor: Resource temporarily unavailable
    bNumInterfaces          1
    Interface Descriptor:
      bInterfaceNumber        0
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0 
can't get debug descriptor: Resource temporarily unavailable
    bNumInterfaces          1
    Interface Descriptor:
      bInterfaceNumber        0
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0 

```
two occurrences because of the CDROM drive... 

I've tried to plug this device into an USB 2.0 port. The frequency of disconnection halved but still disconnect and reconnect.
So in desperation, I plugged the same contraption on Windows 11 on the very same computer and USB 3.1 port. It worked flawlessly and I was able to format, clear copy a huge amount of files on the external disk without problem. 
So the problem lies somewhere in my installation of Ubuntu but I can't find it. 
So I beg for help and will be thankful to get it ! 
In the mean time, have a nice and bright day !

---

