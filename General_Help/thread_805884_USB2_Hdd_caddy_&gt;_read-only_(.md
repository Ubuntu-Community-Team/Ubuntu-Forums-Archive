---
title: "USB2 Hdd caddy &gt; read-only :("
date: 2008-05-24
forum: General Help
---

### Post by mr.z on 2008-05-24
Hi all.

 sure its a common problem but despite much searching can't seem to find anything useful.

 I'm using gusty. For some reason the hdd (from a dead laptop) when mounted is set to "read only" which makes it about as useful as a ladder made of cat piss.

 Is there anything that can make it set and stay set to read and write? so that any ubuntu running machine its plugged into will be able to use i like a big lumpy usb stick drive.

 Thanks for reading

---

### Post by chrisccoulson on 2008-05-24
Is it a FAT32 partition? My guess is that it is.

Could you open a terminal and type in:
```
tail -f /var/log/syslog
```
...and then plug in your hard drive. Monitor the output from the terminal and look for any clues. My guess is that the filesystem has errors, and you'll see a load of lines saying 'Filesystem panic'. If this is the case, then do the following (assuming it is a FAT32 partition):
```
sudo umount /dev/sdxx
sudo dosfsck -a -v /dev/sdxx
```
...where /dev/sdxx is the device node for the partition (you'll probably see it in the terminal above when you monitor your syslog as you plug it in).

If you're not sure, then post the entries you see from your syslog as you connect the drive.

---

### Post by mr.z on 2008-05-24
```
May 24 17:58:17 ZODIARK kernel: [29470.908000] usb 2-1: new full speed USB device using uhci_hcd and address 4
May 24 17:58:17 ZODIARK kernel: [29471.064000] usb 2-1: configuration #1 chosen from 1 choice
May 24 17:58:17 ZODIARK kernel: [29471.068000] scsi4 : SCSI emulation for USB Mass Storage devices
May 24 17:58:17 ZODIARK kernel: [29471.068000] usb-storage: device found at 4
May 24 17:58:17 ZODIARK kernel: [29471.068000] usb-storage: waiting for device to settle before scanning
May 24 17:58:17 ZODIARK NetworkManager: <debug> [1211648297.522590] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2506_0000000000000'). 
May 24 17:58:17 ZODIARK NetworkManager: <debug> [1211648297.682543] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2506_0000000000000_if0'). 
May 24 17:58:17 ZODIARK NetworkManager: <debug> [1211648297.742604] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2506_0000000000000_usbraw'). 
May 24 17:58:22 ZODIARK kernel: [29476.068000] usb-storage: device scan complete
May 24 17:58:22 ZODIARK kernel: [29476.072000] scsi 4:0:0:0: Direct-Access     TOSHIBA  MK2018GAP        M1.4 PQ: 0 ANSI: 0
May 24 17:58:22 ZODIARK kernel: [29476.076000] sd 4:0:0:0: [sdb] 39070080 512-byte hardware sectors (20004 MB)
May 24 17:58:22 ZODIARK kernel: [29476.080000] sd 4:0:0:0: [sdb] Write Protect is off
May 24 17:58:22 ZODIARK kernel: [29476.080000] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
May 24 17:58:22 ZODIARK kernel: [29476.080000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
May 24 17:58:22 ZODIARK kernel: [29476.088000] sd 4:0:0:0: [sdb] 39070080 512-byte hardware sectors (20004 MB)
May 24 17:58:22 ZODIARK kernel: [29476.092000] sd 4:0:0:0: [sdb] Write Protect is off
May 24 17:58:22 ZODIARK kernel: [29476.092000] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
May 24 17:58:22 ZODIARK kernel: [29476.092000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
May 24 17:58:23 ZODIARK kernel: [29476.092000]  sdb: sdb1 sdb2 sdb3 < sdb5 >
May 24 17:58:23 ZODIARK kernel: [29476.608000] sd 4:0:0:0: [sdb] Attached SCSI disk
May 24 17:58:23 ZODIARK kernel: [29476.608000] sd 4:0:0:0: Attached scsi generic sg2 type 0
May 24 17:58:23 ZODIARK NetworkManager: <debug> [1211648303.375962] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2506_0000000000000_if0_scsi_host'). 
May 24 17:58:23 ZODIARK NetworkManager: <debug> [1211648303.384477] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2506_0000000000000_if0_scsi_host_scsi_device_lun0'). 
May 24 17:58:23 ZODIARK NetworkManager: <debug> [1211648303.397243] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2506_0000000000000_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
May 24 17:58:24 ZODIARK NetworkManager: <debug> [1211648304.202805] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_TOSHIBA_MK2018GAP_0000000000000_0_0'). 
May 24 17:58:24 ZODIARK NetworkManager: <debug> [1211648304.808931] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part3_size_1024'). 
May 24 17:58:25 ZODIARK NetworkManager: <debug> [1211648305.061001] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_98E7_3BCC'). 
May 24 17:58:25 ZODIARK NetworkManager: <debug> [1211648305.312387] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_c61459b4_a907_483b_8139_9324f519f96e'). 
May 24 17:58:25 ZODIARK hald: mounted /dev/sdb1 on behalf of uid 1000
May 24 17:58:26 ZODIARK NetworkManager: <debug> [1211648306.515745] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_4838_3811'). 
May 24 17:58:27 ZODIARK hald: mounted /dev/sdb2 on behalf of uid 1000
May 24 17:58:30 ZODIARK kernel: [29484.372000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:30 ZODIARK kernel: [29484.372000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:30 ZODIARK kernel: [29484.372000]     File system has been set read-only
May 24 17:58:30 ZODIARK kernel: [29484.388000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:30 ZODIARK kernel: [29484.388000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:30 ZODIARK kernel: [29484.396000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:30 ZODIARK kernel: [29484.396000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:30 ZODIARK kernel: [29484.408000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:30 ZODIARK kernel: [29484.408000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:30 ZODIARK kernel: [29484.416000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:30 ZODIARK kernel: [29484.416000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:30 ZODIARK kernel: [29484.428000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:30 ZODIARK kernel: [29484.428000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:30 ZODIARK kernel: [29484.436000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:30 ZODIARK kernel: [29484.436000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:30 ZODIARK kernel: [29484.448000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:30 ZODIARK kernel: [29484.448000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:30 ZODIARK kernel: [29484.456000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:30 ZODIARK kernel: [29484.456000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:30 ZODIARK kernel: [29484.468000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:30 ZODIARK kernel: [29484.468000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:30 ZODIARK kernel: [29484.480000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:30 ZODIARK kernel: [29484.480000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:30 ZODIARK kernel: [29484.488000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:30 ZODIARK kernel: [29484.488000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:30 ZODIARK kernel: [29484.500000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:30 ZODIARK kernel: [29484.500000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:30 ZODIARK kernel: [29484.508000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:30 ZODIARK kernel: [29484.508000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:30 ZODIARK kernel: [29484.520000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:30 ZODIARK kernel: [29484.520000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:30 ZODIARK kernel: [29484.528000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:30 ZODIARK kernel: [29484.528000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:30 ZODIARK kernel: [29484.540000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:30 ZODIARK kernel: [29484.540000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:30 ZODIARK kernel: [29484.552000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:30 ZODIARK kernel: [29484.552000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:30 ZODIARK kernel: [29484.560000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.560000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.564000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.564000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.572000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.572000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.576000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.576000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.584000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.584000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.592000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.592000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.600000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.600000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.604000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.604000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.612000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.612000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.620000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.620000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.624000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.624000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.632000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.632000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.636000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.636000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.644000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.644000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.652000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.652000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.656000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.656000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.664000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.664000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.672000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.672000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.676000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.676000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.684000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.684000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.692000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.692000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.696000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.696000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.704000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.704000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.712000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.712000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.716000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.716000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.724000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.724000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.732000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.732000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.736000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.736000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.744000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.744000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.752000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.752000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.756000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.756000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.764000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.764000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.768000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.768000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.776000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.776000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.784000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.784000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.792000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.792000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.796000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.796000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.804000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.804000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.812000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.812000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.816000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.816000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.824000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.824000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.828000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.828000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.836000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.836000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.844000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.844000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.848000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.848000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.856000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.856000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.864000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.864000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.868000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.868000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.876000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.876000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.884000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.884000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.888000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.888000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.896000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.896000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.904000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.904000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.908000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.908000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.916000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.916000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.924000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.924000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.928000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.928000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.936000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.936000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.944000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.944000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.952000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.952000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.960000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.960000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29484.964000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29484.964000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.024000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.024000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.028000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.028000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.036000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.036000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.044000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.044000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.048000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.048000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.056000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.056000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.060000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.060000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.068000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.068000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.076000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.076000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.080000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.080000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.088000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.088000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.092000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.092000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.100000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.100000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.108000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.108000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.112000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.112000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.120000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.120000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.128000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.128000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.132000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.132000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.140000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.140000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.148000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.148000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.156000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.156000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.160000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.160000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.168000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.168000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.172000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.172000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.180000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.180000]     fat_get_cluster: invalid cluster chain (i_pos 867830)
May 24 17:58:31 ZODIARK kernel: [29485.188000] FAT: Filesystem panic (dev sdb1)
May 24 17:58:31 ZODIARK kernel: [29485.188000]     fat_get_cluster: invalid cluster chain (i_pos 867830)



```

Hope that makes sense ^__^

Would some other file system work better? ext2/3? fat16 even?

I'd not mind that, could leave 2gig free for windows rubbish for uni e.t.c.

---

### Post by chrisccoulson on 2008-05-24
The problem is that it was probably not cleanly unmounted. That's usually a trigger for these errors, and FAT isn't a very robust filesystem. But, to fix it:
```
sudo umount /dev/sdb1
sudo dosfsck -a -v /dev/sdb1
```

---

### Post by mr.z on 2008-05-24
thanks for that.

its got one of the two partitions to read/write

would it be worth formating them to ext 2 / 3 (don't know the difference tbh) would this allow more of a plug in and go arrangement?

Thanks for the help

---

