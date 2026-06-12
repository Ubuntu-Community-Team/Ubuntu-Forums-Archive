---
title: "Ipod and Removable Media desktop icons disapeared"
date: 2008-07-03
forum: General Help
---

### Post by ironwolfe on 2008-07-03
When i plug in my ipod or thumb drives into my gutsy box, they mount properly in /media and I can access them from the Computer window, but a desktop icon is not created for them any more...

It is weird, but everything works well - I can eject, mount, read, etc. when the ipod or drive is hot plugged - just no icon on desktop...

any ideas?

here is some dmesg output from the last few plug ins of a 30Gb and 60GB ipods.

```
[  587.636000] usb 2-3: new high speed USB device using ehci_hcd and address 6
[  587.768000] usb 2-3: configuration #1 chosen from 2 choices
[  587.852000] usbcore: registered new interface driver libusual
[  587.868000] Initializing USB Mass Storage driver...
[  587.872000] scsi8 : SCSI emulation for USB Mass Storage devices
[  587.872000] usb-storage: device found at 6
[  587.872000] usb-storage: waiting for device to settle before scanning
[  587.872000] usbcore: registered new interface driver usb-storage
[  587.872000] USB Mass Storage support registered.
[  592.872000] usb-storage: device scan complete
[  592.872000] scsi 8:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[  592.876000] sd 8:0:0:0: [sdf] 58605120 512-byte hardware sectors (30006 MB)
[  592.880000] sd 8:0:0:0: [sdf] Write Protect is off
[  592.880000] sd 8:0:0:0: [sdf] Mode Sense: 68 00 00 08
[  592.880000] sd 8:0:0:0: [sdf] Assuming drive cache: write through
[  592.880000] sd 8:0:0:0: [sdf] 58605120 512-byte hardware sectors (30006 MB)
[  592.884000] sd 8:0:0:0: [sdf] Write Protect is off
[  592.884000] sd 8:0:0:0: [sdf] Mode Sense: 68 00 00 08
[  592.884000] sd 8:0:0:0: [sdf] Assuming drive cache: write through
[  592.884000]  sdf: sdf1 sdf2
[  592.904000] sd 8:0:0:0: [sdf] Attached SCSI removable disk
[  592.904000] sd 8:0:0:0: Attached scsi generic sg5 type 0
[ 2938.644000] usb 2-3: USB disconnect, address 6
[61001.568000] usb 2-3: new high speed USB device using ehci_hcd and address 7
[61001.700000] usb 2-3: configuration #1 chosen from 1 choice
[61001.700000] scsi9 : SCSI emulation for USB Mass Storage devices
[61001.700000] usb-storage: device found at 7
[61001.700000] usb-storage: waiting for device to settle before scanning
[61006.700000] usb-storage: device scan complete
[61006.700000] scsi 9:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[61006.700000] sd 9:0:0:0: [sdf] 117210239 512-byte hardware sectors (60012 MB)
[61006.704000] sd 9:0:0:0: [sdf] Write Protect is off
[61006.704000] sd 9:0:0:0: [sdf] Mode Sense: 64 00 00 08
[61006.704000] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[61006.708000] sd 9:0:0:0: [sdf] 117210239 512-byte hardware sectors (60012 MB)
[61006.708000] sd 9:0:0:0: [sdf] Write Protect is off
[61006.708000] sd 9:0:0:0: [sdf] Mode Sense: 64 00 00 08
[61006.708000] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[61006.708000]  sdf: sdf1 sdf2
[61006.720000]  sdf: p2 exceeds device capacity
[61006.720000] sd 9:0:0:0: [sdf] Attached SCSI removable disk
[61006.720000] sd 9:0:0:0: Attached scsi generic sg5 type 0
[61007.024000] attempt to access beyond end of device
[61007.024000] sdf: rw=0, want=117210240, limit=117210239
[61007.024000] Buffer I/O error on device sdf2, logical block 117129914
[61007.028000] attempt to access beyond end of device
[61007.028000] sdf: rw=0, want=117210240, limit=117210239
[61007.028000] Buffer I/O error on device sdf2, logical block 117129914
[61007.028000] attempt to access beyond end of device
[61007.028000] sdf: rw=0, want=117210240, limit=117210239
[61007.028000] Buffer I/O error on device sdf2, logical block 117129914
[61007.028000] attempt to access beyond end of device
[61007.028000] sdf: rw=0, want=117210240, limit=117210239
[61007.028000] Buffer I/O error on device sdf2, logical block 117129914
[61007.032000] attempt to access beyond end of device
[61007.032000] sdf: rw=0, want=117210240, limit=117210239
[61007.032000] Buffer I/O error on device sdf2, logical block 117129914
[61007.032000] attempt to access beyond end of device
[61007.032000] sdf: rw=0, want=117210240, limit=117210239
[61007.032000] Buffer I/O error on device sdf2, logical block 117129914
[61007.032000] attempt to access beyond end of device
[61007.032000] sdf: rw=0, want=117210240, limit=117210239
[61007.032000] Buffer I/O error on device sdf2, logical block 117129914
[61007.152000] attempt to access beyond end of device
[61007.152000] sdf: rw=0, want=117210240, limit=117210239
[61007.152000] Buffer I/O error on device sdf2, logical block 117129914
[61007.152000] attempt to access beyond end of device
[61007.152000] sdf: rw=0, want=117210240, limit=117210239
[61007.152000] Buffer I/O error on device sdf2, logical block 117129914
[61007.268000] attempt to access beyond end of device
[61007.268000] sdf: rw=0, want=117210240, limit=117210239
[61007.268000] Buffer I/O error on device sdf2, logical block 117129914
[61007.296000] attempt to access beyond end of device
[61007.296000] sdf: rw=0, want=117210240, limit=117210239
[61007.296000] attempt to access beyond end of device
[61007.296000] sdf: rw=0, want=117210240, limit=117210239
[61007.296000] attempt to access beyond end of device
[61007.296000] sdf: rw=0, want=117210240, limit=117210239
[61007.296000] attempt to access beyond end of device
[61007.296000] sdf: rw=0, want=117210240, limit=117210239
[61007.296000] attempt to access beyond end of device
[61007.296000] sdf: rw=0, want=117210240, limit=117210239
[61007.296000] attempt to access beyond end of device
[61007.296000] sdf: rw=0, want=117210240, limit=117210239
[61007.340000] attempt to access beyond end of device
[61007.340000] sdf: rw=0, want=117210240, limit=117210239
[61007.340000] attempt to access beyond end of device
[61007.340000] sdf: rw=0, want=117210240, limit=117210239
[71179.696000] sd 9:0:0:0: [sdf] 117210239 512-byte hardware sectors (60012 MB)
[71179.700000] sd 9:0:0:0: [sdf] Write Protect is off
[71179.700000] sd 9:0:0:0: [sdf] Mode Sense: 64 00 00 08
[71179.700000] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[71181.696000] sd 9:0:0:0: [sdf] 117210239 512-byte hardware sectors (60012 MB)
[71181.700000] sd 9:0:0:0: [sdf] Write Protect is off
[71181.700000] sd 9:0:0:0: [sdf] Mode Sense: 64 00 00 08
[71181.700000] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[74706.212000] sd 9:0:0:0: [sdf] 117210239 512-byte hardware sectors (60012 MB)
[74706.268000] sd 9:0:0:0: [sdf] Write Protect is off
[74706.268000] sd 9:0:0:0: [sdf] Mode Sense: 64 00 00 08
[74706.268000] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[74706.268000]  sdf: sdf1 sdf2
[74706.340000]  sdf: p2 exceeds device capacity
[74706.452000] attempt to access beyond end of device
[74706.452000] sdf: rw=0, want=117210240, limit=117210239
[74706.452000] printk: 8 messages suppressed.
[74706.452000] Buffer I/O error on device sdf2, logical block 117129914
[74706.468000] attempt to access beyond end of device
[74706.468000] sdf: rw=0, want=117210240, limit=117210239
[74706.468000] Buffer I/O error on device sdf2, logical block 117129914
[74706.468000] attempt to access beyond end of device
[74706.468000] sdf: rw=0, want=117210240, limit=117210239
[74706.468000] Buffer I/O error on device sdf2, logical block 117129914
[74706.472000] attempt to access beyond end of device
[74706.472000] sdf: rw=0, want=117210240, limit=117210239
[74706.472000] Buffer I/O error on device sdf2, logical block 117129914
[74706.472000] attempt to access beyond end of device
[74706.472000] sdf: rw=0, want=117210240, limit=117210239
[74706.472000] Buffer I/O error on device sdf2, logical block 117129914
[74706.472000] attempt to access beyond end of device
[74706.472000] sdf: rw=0, want=117210240, limit=117210239
[74706.472000] Buffer I/O error on device sdf2, logical block 117129914
[74706.472000] attempt to access beyond end of device
[74706.472000] sdf: rw=0, want=117210240, limit=117210239
[74706.472000] Buffer I/O error on device sdf2, logical block 117129914
[74706.600000] attempt to access beyond end of device
[74706.600000] sdf: rw=0, want=117210240, limit=117210239
[74706.600000] Buffer I/O error on device sdf2, logical block 117129914
[74706.600000] attempt to access beyond end of device
[74706.600000] sdf: rw=0, want=117210240, limit=117210239
[74706.600000] Buffer I/O error on device sdf2, logical block 117129914
[74706.812000] attempt to access beyond end of device
[74706.812000] sdf: rw=0, want=117210240, limit=117210239
[74706.812000] Buffer I/O error on device sdf2, logical block 117129914
[74706.812000] attempt to access beyond end of device
[74706.812000] sdf: rw=0, want=117210240, limit=117210239
[74706.816000] attempt to access beyond end of device
[74706.816000] sdf: rw=0, want=117210240, limit=117210239
[74706.816000] attempt to access beyond end of device
[74706.816000] sdf: rw=0, want=117210240, limit=117210239
[74706.816000] attempt to access beyond end of device
[74706.816000] sdf: rw=0, want=117210240, limit=117210239
[74706.816000] attempt to access beyond end of device
[74706.816000] sdf: rw=0, want=117210240, limit=117210239
[74706.816000] attempt to access beyond end of device
[74706.816000] sdf: rw=0, want=117210240, limit=117210239
[74706.884000] attempt to access beyond end of device
[74706.884000] sdf: rw=0, want=117210240, limit=117210239
[74706.884000] attempt to access beyond end of device
[74706.884000] sdf: rw=0, want=117210240, limit=117210239
[84299.728000] usb 2-3: USB disconnect, address 7
[84791.136000] usb 2-3: new high speed USB device using ehci_hcd and address 8
[84791.268000] usb 2-3: configuration #1 chosen from 2 choices
[84791.332000] scsi10 : SCSI emulation for USB Mass Storage devices
[84791.332000] usb-storage: device found at 8
[84791.332000] usb-storage: waiting for device to settle before scanning
[84796.332000] usb-storage: device scan complete
[84796.332000] scsi 10:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[84796.336000] sd 10:0:0:0: [sdf] 58605120 512-byte hardware sectors (30006 MB)
[84796.336000] sd 10:0:0:0: [sdf] Write Protect is off
[84796.336000] sd 10:0:0:0: [sdf] Mode Sense: 68 00 00 08
[84796.336000] sd 10:0:0:0: [sdf] Assuming drive cache: write through
[84796.340000] sd 10:0:0:0: [sdf] 58605120 512-byte hardware sectors (30006 MB)
[84796.344000] sd 10:0:0:0: [sdf] Write Protect is off
[84796.344000] sd 10:0:0:0: [sdf] Mode Sense: 68 00 00 08
[84796.344000] sd 10:0:0:0: [sdf] Assuming drive cache: write through
[84796.344000]  sdf: sdf1 sdf2
[84796.360000] sd 10:0:0:0: [sdf] Attached SCSI removable disk
[84796.360000] sd 10:0:0:0: Attached scsi generic sg5 type 0
[86069.888000] usb 2-3: USB disconnect, address 8
[86074.056000] usb 2-3: new high speed USB device using ehci_hcd and address 9
[86074.192000] usb 2-3: configuration #1 chosen from 2 choices
[86074.192000] scsi11 : SCSI emulation for USB Mass Storage devices
[86074.192000] usb-storage: device found at 9
[86074.192000] usb-storage: waiting for device to settle before scanning
[86079.192000] usb-storage: device scan complete
[86079.192000] scsi 11:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[86079.196000] sd 11:0:0:0: [sdf] 58605120 512-byte hardware sectors (30006 MB)
[86079.196000] sd 11:0:0:0: [sdf] Write Protect is off
[86079.200000] sd 11:0:0:0: [sdf] Mode Sense: 68 00 00 08
[86079.200000] sd 11:0:0:0: [sdf] Assuming drive cache: write through
[86079.204000] sd 11:0:0:0: [sdf] 58605120 512-byte hardware sectors (30006 MB)
[86079.204000] sd 11:0:0:0: [sdf] Write Protect is off
[86079.208000] sd 11:0:0:0: [sdf] Mode Sense: 68 00 00 08
[86079.208000] sd 11:0:0:0: [sdf] Assuming drive cache: write through
[86079.208000]  sdf: sdf1 sdf2
[86079.248000] sd 11:0:0:0: [sdf] Attached SCSI removable disk
[86079.248000] sd 11:0:0:0: Attached scsi generic sg5 type 0
[86167.472000] usb 2-3: USB disconnect, address 9
[86170.392000] usb 2-3: new high speed USB device using ehci_hcd and address 10
[86170.524000] usb 2-3: configuration #1 chosen from 2 choices
[86170.524000] scsi12 : SCSI emulation for USB Mass Storage devices
[86170.524000] usb-storage: device found at 10
[86170.524000] usb-storage: waiting for device to settle before scanning
[86175.524000] usb-storage: device scan complete
[86175.524000] scsi 12:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[86175.528000] sd 12:0:0:0: [sdf] 58605120 512-byte hardware sectors (30006 MB)
[86175.528000] sd 12:0:0:0: [sdf] Write Protect is off
[86175.528000] sd 12:0:0:0: [sdf] Mode Sense: 68 00 00 08
[86175.528000] sd 12:0:0:0: [sdf] Assuming drive cache: write through
[86175.532000] sd 12:0:0:0: [sdf] 58605120 512-byte hardware sectors (30006 MB)
[86175.536000] sd 12:0:0:0: [sdf] Write Protect is off
[86175.536000] sd 12:0:0:0: [sdf] Mode Sense: 68 00 00 08
[86175.536000] sd 12:0:0:0: [sdf] Assuming drive cache: write through
[86175.536000]  sdf: sdf1 sdf2
[86175.552000] sd 12:0:0:0: [sdf] Attached SCSI removable disk
[86175.552000] sd 12:0:0:0: Attached scsi generic sg5 type 0
[87117.716000] FAT: Unrecognized mount option "gid" or missing value
[87197.388000] usb 2-3: USB disconnect, address 10
[87204.740000] usb 2-3: new high speed USB device using ehci_hcd and address 11
[87204.872000] usb 2-3: configuration #1 chosen from 2 choices
[87204.872000] scsi13 : SCSI emulation for USB Mass Storage devices
[87204.872000] usb-storage: device found at 11
[87204.872000] usb-storage: waiting for device to settle before scanning
[87209.872000] usb-storage: device scan complete
[87209.872000] scsi 13:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[87209.876000] sd 13:0:0:0: [sdf] 58605120 512-byte hardware sectors (30006 MB)
[87209.880000] sd 13:0:0:0: [sdf] Write Protect is off
[87209.880000] sd 13:0:0:0: [sdf] Mode Sense: 68 00 00 08
[87209.880000] sd 13:0:0:0: [sdf] Assuming drive cache: write through
[87209.884000] sd 13:0:0:0: [sdf] 58605120 512-byte hardware sectors (30006 MB)
[87209.888000] sd 13:0:0:0: [sdf] Write Protect is off
[87209.888000] sd 13:0:0:0: [sdf] Mode Sense: 68 00 00 08
[87209.888000] sd 13:0:0:0: [sdf] Assuming drive cache: write through
[87209.888000]  sdf: sdf1 sdf2
[87209.920000] sd 13:0:0:0: [sdf] Attached SCSI removable disk
[87209.920000] sd 13:0:0:0: Attached scsi generic sg5 type 0
[87239.616000] usb 2-3: USB disconnect, address 11
[87243.400000] usb 2-3: new high speed USB device using ehci_hcd and address 12
[87243.532000] usb 2-3: configuration #1 chosen from 2 choices
[87243.532000] scsi14 : SCSI emulation for USB Mass Storage devices
[87243.536000] usb-storage: device found at 12
[87243.536000] usb-storage: waiting for device to settle before scanning
[87248.536000] usb-storage: device scan complete
[87248.536000] scsi 14:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[87248.540000] sd 14:0:0:0: [sdf] 58605120 512-byte hardware sectors (30006 MB)
[87248.544000] sd 14:0:0:0: [sdf] Write Protect is off
[87248.544000] sd 14:0:0:0: [sdf] Mode Sense: 68 00 00 08
[87248.544000] sd 14:0:0:0: [sdf] Assuming drive cache: write through
[87248.548000] sd 14:0:0:0: [sdf] 58605120 512-byte hardware sectors (30006 MB)
[87248.552000] sd 14:0:0:0: [sdf] Write Protect is off
[87248.552000] sd 14:0:0:0: [sdf] Mode Sense: 68 00 00 08
[87248.552000] sd 14:0:0:0: [sdf] Assuming drive cache: write through
[87248.552000]  sdf: sdf1 sdf2
[87248.584000] sd 14:0:0:0: [sdf] Attached SCSI removable disk
[87248.584000] sd 14:0:0:0: Attached scsi generic sg5 type 0
[87308.464000] usb 2-3: USB disconnect, address 12
[87313.892000] usb 2-3: new high speed USB device using ehci_hcd and address 13
[87314.024000] usb 2-3: configuration #1 chosen from 2 choices
[87314.024000] scsi15 : SCSI emulation for USB Mass Storage devices
[87314.024000] usb-storage: device found at 13
[87314.024000] usb-storage: waiting for device to settle before scanning
[87319.024000] usb-storage: device scan complete
[87319.024000] scsi 15:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[87319.028000] sd 15:0:0:0: [sdf] 58605120 512-byte hardware sectors (30006 MB)
[87319.028000] sd 15:0:0:0: [sdf] Write Protect is off
[87319.028000] sd 15:0:0:0: [sdf] Mode Sense: 68 00 00 08
[87319.028000] sd 15:0:0:0: [sdf] Assuming drive cache: write through
[87319.032000] sd 15:0:0:0: [sdf] 58605120 512-byte hardware sectors (30006 MB)
[87319.036000] sd 15:0:0:0: [sdf] Write Protect is off
[87319.036000] sd 15:0:0:0: [sdf] Mode Sense: 68 00 00 08
[87319.036000] sd 15:0:0:0: [sdf] Assuming drive cache: write through
[87319.036000]  sdf: sdf1 sdf2
[87319.044000] sd 15:0:0:0: [sdf] Attached SCSI removable disk
[87319.044000] sd 15:0:0:0: Attached scsi generic sg5 type 0
[88295.236000] usb 2-3: USB disconnect, address 13
[88309.260000] usb 2-3: new high speed USB device using ehci_hcd and address 14
[88309.392000] usb 2-3: configuration #1 chosen from 2 choices
[88309.392000] scsi16 : SCSI emulation for USB Mass Storage devices
[88309.392000] usb-storage: device found at 14
[88309.392000] usb-storage: waiting for device to settle before scanning
[88314.392000] usb-storage: device scan complete
[88314.392000] scsi 16:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[88314.396000] sd 16:0:0:0: [sdf] 58605120 512-byte hardware sectors (30006 MB)
[88314.396000] sd 16:0:0:0: [sdf] Write Protect is off
[88314.396000] sd 16:0:0:0: [sdf] Mode Sense: 68 00 00 08
[88314.396000] sd 16:0:0:0: [sdf] Assuming drive cache: write through
[88314.404000] sd 16:0:0:0: [sdf] 58605120 512-byte hardware sectors (30006 MB)
[88314.404000] sd 16:0:0:0: [sdf] Write Protect is off
[88314.404000] sd 16:0:0:0: [sdf] Mode Sense: 68 00 00 08
[88314.404000] sd 16:0:0:0: [sdf] Assuming drive cache: write through
[88314.404000]  sdf: sdf1 sdf2
[88314.420000] sd 16:0:0:0: [sdf] Attached SCSI removable disk
[88314.420000] sd 16:0:0:0: Attached scsi generic sg5 type 0
[88609.248000] usb 2-3: USB disconnect, address 14

```

Is there a Hald log somewhere where an error might show up?

Thanks!

---

### Post by bmac on 2008-07-03
Just a thought, do any of your mounted drives show up on desktop? If not check Gnome Configuration Editor (Applications/Other)
apps/nautilus/desktop/volumes_visible (check box)


Hope this helps....

---

### Post by soccerboy on 2008-07-03
can access gnome configuration editor by hitting Alt+F2 and then typing gconf-editor.

---

### Post by ironwolfe on 2008-07-25
I have turned this on and off many times - no luck.

---

