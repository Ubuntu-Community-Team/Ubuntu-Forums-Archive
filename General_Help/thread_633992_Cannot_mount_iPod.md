---
title: "Cannot mount iPod"
date: 2007-12-07
forum: General Help
---

### Post by jchien on 2007-12-07
I'm running Fiesty Fawn and have a 4th generation iPod that used to auto-mount and show up on my desktop without problem.

However, now it doesn't seem to auto-mount anymore. When I connect my iPod it shows the main menu instead of the "do not disconnect" warning. I've tried doing
```

killall gnome-volume-manager
gnome-volume-manager
```

but that didn't solve the problem. Also my
```
dmesg | tail
```
doesn't look like any of the others I've seen, and says
```
[ 1616.944000] usb 4-3: new high speed USB device using ehci_hcd and address 90
[ 1618.456000] usb 4-3: new high speed USB device using ehci_hcd and address 95
[ 1619.716000] usb 4-3: new high speed USB device using ehci_hcd and address 99
[ 1621.480000] usb 4-3: new high speed USB device using ehci_hcd and address 105
[ 1624.504000] usb 4-3: new high speed USB device using ehci_hcd and address 116
[ 1822.436000] usb 4-3: new high speed USB device using ehci_hcd and address 122
[ 1823.444000] usb 4-3: new high speed USB device using ehci_hcd and address 125
[ 1823.704000] ehci_hcd 0000:00:1d.7: port 3 reset error -110
[ 1823.704000] hub 4-0:1.0: hub_port_status failed (err = -32)
[ 1824.956000] usb 4-3: new high speed USB device using ehci_hcd and address 2

```

I haven't really tried attaching any other USB devices, though. On my Windows machine my iPod mounts as an external drive just fine. Anyone know what to make of this?

---

### Post by Prospero2006 on 2007-12-07
ipods usually show up on /dev/sda2 or /dev/sdb2 or /dev/sdc2  etc...

so 
try this 
```

dmesg | grep sd


```

See if you get anything there

then create a directory /media/ipod

then
```

mount /dev/sda2 /media/ipod

```

Anything?

Pros

---

### Post by rod40cool on 2008-02-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I confirm this problem with my new install of Gutsy AMD 64 bit.
Ipod keeps mounting then unmounting after about 5 mins.
Feb 11 23:16:43 rod-desk64 kernel: [  215.846909] usb 2-6: USB disconnect, address 8
Feb 11 23:16:47 rod-desk64 kernel: [  217.781089] usb 2-6: new high speed USB device using ehci_hcd and address 9
Feb 11 23:16:47 rod-desk64 kernel: [  217.940249] usb 2-6: configuration #1 chosen from 1 choice
Feb 11 23:16:47 rod-desk64 kernel: [  217.940410] scsi6 : SCSI emulation for USB Mass Storage devices
Feb 11 23:16:52 rod-desk64 kernel: [  220.212503] scsi 6:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Feb 11 23:16:52 rod-desk64 kernel: [  220.213611] sd 6:0:0:0: [sdb] 39063023 512-byte hardware sectors (20000 MB)
Feb 11 23:16:53 rod-desk64 kernel: [  220.266530] usb 2-6: reset high speed USB device using ehci_hcd and address 9
Feb 11 23:16:53 rod-desk64 kernel: [  220.327060] usb 2-6: device firmware changed
Feb 11 23:16:53 rod-desk64 kernel: [  220.327073] usb 2-6: USB disconnect, address 9
Feb 11 23:16:53 rod-desk64 kernel: [  220.327094] sd 6:0:0:0: [sdb] Write Protect is off
Feb 11 23:16:53 rod-desk64 kernel: [  220.327225] sd 6:0:0:0: [sdb] READ CAPACITY failed
Feb 11 23:16:53 rod-desk64 kernel: [  220.327228] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Feb 11 23:16:53 rod-desk64 kernel: [  220.327232] sd 6:0:0:0: [sdb] Sense not available.
Feb 11 23:16:53 rod-desk64 kernel: [  220.327252] sd 6:0:0:0: [sdb] Write Protect is off
Feb 11 23:16:53 rod-desk64 kernel: [  220.327331] sd 6:0:0:0: [sdb] READ CAPACITY failed
Feb 11 23:16:53 rod-desk64 kernel: [  220.327333] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Feb 11 23:16:53 rod-desk64 kernel: [  220.327336] sd 6:0:0:0: [sdb] Sense not available.
Feb 11 23:16:53 rod-desk64 kernel: [  220.327356] sd 6:0:0:0: [sdb] Write Protect is off
Feb 11 23:16:53 rod-desk64 kernel: [  220.327389] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Feb 11 23:16:53 rod-desk64 kernel: [  220.327431] sd 6:0:0:0: Attached scsi generic sg1 type 0
Feb 11 23:16:53 rod-desk64 kernel: [  220.379186] usb 2-6: new high speed USB device using ehci_hcd and address 10
Feb 11 23:16:53 rod-desk64 kernel: [  220.440186] usb 2-6: configuration #1 chosen from 1 choice
Feb 11 23:16:53 rod-desk64 kernel: [  220.440342] scsi7 : SCSI emulation for USB Mass Storage devices
Feb 11 23:16:58 rod-desk64 kernel: [  222.712443] scsi 7:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Feb 11 23:16:58 rod-desk64 kernel: [  222.713279] sd 7:0:0:0: [sdb] 39063023 512-byte hardware sectors (20000 MB)
Feb 11 23:16:58 rod-desk64 kernel: [  222.713736] sd 7:0:0:0: [sdb] Write Protect is off
Feb 11 23:16:58 rod-desk64 kernel: [  222.714555] sd 7:0:0:0: [sdb] 39063023 512-byte hardware sectors (20000 MB)
Feb 11 23:16:58 rod-desk64 kernel: [  222.715057] sd 7:0:0:0: [sdb] Write Protect is off
Feb 11 23:16:58 rod-desk64 kernel: [  222.715069]  sdb: sdb1 sdb2
Feb 11 23:16:58 rod-desk64 kernel: [  222.719812] sd 7:0:0:0: [sdb] Attached SCSI removable disk
Feb 11 23:16:58 rod-desk64 kernel: [  222.719854] sd 7:0:0:0: Attached scsi generic sg1 type 0
Feb 11 23:17:38 rod-desk64 kernel: [  243.617572] usb 2-6: reset high speed USB device using ehci_hcd and address 10
Feb 11 23:18:41 rod-desk64 kernel: [  273.387337] usb 2-6: reset high speed USB device using ehci_hcd and address 10
Feb 11 23:18:51 rod-desk64 kernel: [  278.134679] usb 2-6: reset high speed USB device using ehci_hcd and address 10
Feb 11 23:18:52 rod-desk64 kernel: [  278.194941] usb 2-6: USB disconnect, address 10
Feb 11 23:18:52 rod-desk64 kernel: [  278.194949] sd 7:0:0:0: scsi: Device offlined - not ready after error recovery
Feb 11 23:18:52 rod-desk64 kernel: [  278.194958] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Feb 11 23:18:52 rod-desk64 kernel: [  278.194961] end_request: I/O error, dev sdb, sector 85049
Feb 11 23:18:52 rod-desk64 kernel: [  278.252801] usb 2-6: new high speed USB device using ehci_hcd and address 11
Feb 11 23:18:52 rod-desk64 kernel: [  278.314181] usb 2-6: configuration #1 chosen from 1 choice
Feb 11 23:18:52 rod-desk64 kernel: [  278.314337] scsi8 : SCSI emulation for USB Mass Storage devices
Feb 11 23:18:57 rod-desk64 kernel: [  281.260746] scsi 8:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Feb 11 23:18:57 rod-desk64 kernel: [  281.262659] sd 8:0:0:0: [sdb] 39063023 512-byte hardware sectors (20000 MB)
Feb 11 23:18:57 rod-desk64 kernel: [  281.263113] sd 8:0:0:0: [sdb] Write Protect is off
Feb 11 23:18:57 rod-desk64 kernel: [  281.263793] sd 8:0:0:0: [sdb] 39063023 512-byte hardware sectors (20000 MB)
Feb 11 23:18:57 rod-desk64 kernel: [  281.264247] sd 8:0:0:0: [sdb] Write Protect is off
Feb 11 23:18:59 rod-desk64 kernel: [  281.264254]  sdb: sdb1 sdb2
Feb 11 23:18:59 rod-desk64 kernel: [  282.161169] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Feb 11 23:18:59 rod-desk64 kernel: [  282.161210] sd 8:0:0:0: Attached scsi generic sg1 type 0

The suggestion to 'sudo modprobe -r ehci_hcd is a work-around but USB transfer rate drops. Not ideal when you're trying to load up GB of music to an iPod.

Rod

---

### Post by Keith Hedger on 2008-02-11
Ive somtimes had problems with my iPod automounting and Ive found that just putting it into disk mode before plugging it in seems to work ok

---

