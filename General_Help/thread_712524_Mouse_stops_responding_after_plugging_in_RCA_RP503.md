---
title: "Mouse stops responding after plugging in RCA RP5035A"
date: 2008-03-01
forum: General Help
---

### Post by kvdbreem on 2008-03-01
Strange bug and not sure where to post:

1.  Plug in RCA voice recorder (model RP5035A
2.  Window pops up with contents
3.  Mouse stops responding.  Checked dmesg output but forgot to get a copy of it for post.  Will do that later on next reproduction of error.

System environment:
Dell Dimension 8400, 
mouse is logitec wireless, 
using flatscreen monitor side port for USB for mouse,
Using dell front USB port (under the logo thing that can be flipped on the front) for plugging in RCA recorder

Any thoughts?

---

### Post by kvdbreem on 2008-03-02
Here is the output from dmesg.  This time, I wiggled my mouse around as the device was mounting.  It didn't freeze up this time.  

```

[26517.510094] scsi 6:0:0:0: Direct-Access              RCA_TKCF2494_US  1.00 PQ: 0 ANSI: 0 CCS
[26517.515068] sd 6:0:0:0: [sdb] 251136 512-byte hardware sectors (129 MB)
[26517.518048] sd 6:0:0:0: [sdb] Write Protect is off
[26517.518054] sd 6:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[26517.518058] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[26517.527021] sd 6:0:0:0: [sdb] 251136 512-byte hardware sectors (129 MB)
[26517.530017] sd 6:0:0:0: [sdb] Write Protect is off
[26517.530023] sd 6:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[26517.530027] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[26517.530036]  sdb: sdb1
[26517.583884] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[26517.583944] sd 6:0:0:0: Attached scsi generic sg3 type 0
[26518.972790] usb 1-7.1: reset full speed USB device using ehci_hcd and address 11
[26524.475381] hub 1-7:1.0: cannot reset port 1 (err = -71)
[26524.675265] hub 1-7:1.0: hub_port_status failed (err = -71)
[26524.934466] usb 1-7.1: reset full speed USB device using ehci_hcd and address 11
[26525.285375] usb 1-7.2: reset low speed USB device using ehci_hcd and address 12

```

---

### Post by kvdbreem on 2008-03-02
The mouse froze again when I tried to perform i/o on the device.  Here's the updated dmesg:

```

[26517.510094] scsi 6:0:0:0: Direct-Access              RCA_TKCF2494_US  1.00 PQ: 0 ANSI: 0 CCS
[26517.515068] sd 6:0:0:0: [sdb] 251136 512-byte hardware sectors (129 MB)
[26517.518048] sd 6:0:0:0: [sdb] Write Protect is off
[26517.518054] sd 6:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[26517.518058] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[26517.527021] sd 6:0:0:0: [sdb] 251136 512-byte hardware sectors (129 MB)
[26517.530017] sd 6:0:0:0: [sdb] Write Protect is off
[26517.530023] sd 6:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[26517.530027] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[26517.530036]  sdb: sdb1
[26517.583884] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[26517.583944] sd 6:0:0:0: Attached scsi generic sg3 type 0
[26518.972790] usb 1-7.1: reset full speed USB device using ehci_hcd and address 11
[26524.475381] hub 1-7:1.0: cannot reset port 1 (err = -71)
[26524.675265] hub 1-7:1.0: hub_port_status failed (err = -71)
[26524.934466] usb 1-7.1: reset full speed USB device using ehci_hcd and address 11
[26525.285375] usb 1-7.2: reset low speed USB device using ehci_hcd and address 12
[26737.829369] loop: module loaded
[26737.890662] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
[26798.099729] hub 1-0:1.0: port 7 disabled by hub (EMI?), re-enabling...
[26798.099740] usb 1-7: USB disconnect, address 10
[26798.099745] usb 1-7.1: USB disconnect, address 11
[26798.100484] usb 1-7.2: USB disconnect, address 12
[26798.209960] usb 1-7: new high speed USB device using ehci_hcd and address 14
[26798.342137] usb 1-7: configuration #1 chosen from 1 choice
[26798.342314] hub 1-7:1.0: USB hub found
[26798.342402] hub 1-7:1.0: 4 ports detected
[26798.342905] hub 1-7:1.0: hub_hub_status failed (err = -71)
[26798.342914] hub 1-7:1.0: config failed, can't get hub status (err -71)
[27037.613786] /dev/vmmon[12059]: host clock rate change request 83 -> 0
[27037.622876] vmmon: Had to deallocate locked 46754 pages from vm driver efbcc000
[27037.632227] vmmon: Had to deallocate AWE 4565 pages from vm driver efbcc000
[27038.264315] device eth0 left promiscuous mode
[27038.264326] audit(1204446432.817:6): dev=eth0 prom=0 old_prom=256 auid=4294967295
[27038.264330] bridge-eth0: disabled promiscuous mode
[27078.332503] usb 2-2: USB disconnect, address 2

```

---

