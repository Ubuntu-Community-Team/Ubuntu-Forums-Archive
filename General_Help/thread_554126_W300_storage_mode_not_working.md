---
title: "W300 storage mode not working"
date: 2007-09-18
forum: General Help
---

### Post by Lunks on 2007-09-18
Hi, I have a W300 which has a "file manager" mode, which restarts phone to a removable storage device with 2 'partitions': Phone and Phone Card.

For some reason, they don't work anymore. :(
I can manually mount them, but automatically they don't work anymore. They show up on "Computer", but soon disappear.

dmesg output from the time I plug it in:
```

[ 2022.121603] usb 2-2: new full speed USB device using ohci_hcd and address 5
[ 2022.345780] usb 2-2: configuration #1 chosen from 1 choice
[ 2022.351760] cdc_acm 2-2:1.1: ttyACM0: USB ACM device
[ 2022.363831] cdc_acm 2-2:1.3: ttyACM1: USB ACM device
[ 2029.211113] usb 2-2: USB disconnect, address 5
[ 2034.449736] usb 2-2: new full speed USB device using ohci_hcd and address 6
[ 2034.674701] usb 2-2: configuration #1 chosen from 1 choice
[ 2034.677838] scsi2 : SCSI emulation for USB Mass Storage devices
[ 2034.677908] usb-storage: device found at 6
[ 2034.677910] usb-storage: waiting for device to settle before scanning
[ 2034.680784] scsi3 : SCSI emulation for USB Mass Storage devices
[ 2034.680854] usb-storage: device found at 6
[ 2034.680856] usb-storage: waiting for device to settle before scanning
[ 2039.676313] usb-storage: device scan complete
[ 2039.676434] usb-storage: device scan complete
[ 2039.680315] scsi 2:0:0:0: Direct-Access     SEMC     Int.Memory       0000 PQ: 0 ANSI: 0
[ 2039.680354] scsi 3:0:0:0: Direct-Access     SEMC     Mem-Stick        0000 PQ: 0 ANSI: 0
[ 2039.693271] sd 2:0:0:0: [sda] 48000 512-byte hardware sectors (25 MB)
[ 2039.701273] sd 2:0:0:0: [sda] Write Protect is off
[ 2039.701278] sd 2:0:0:0: [sda] Mode Sense: 00 6a 00 00
[ 2039.701280] sd 2:0:0:0: [sda] Assuming drive cache: write through
[ 2039.711334] sd 2:0:0:0: [sda] 48000 512-byte hardware sectors (25 MB)
[ 2039.719254] sd 2:0:0:0: [sda] Write Protect is off
[ 2039.719258] sd 2:0:0:0: [sda] Mode Sense: 00 6a 00 00
[ 2039.719260] sd 2:0:0:0: [sda] Assuming drive cache: write through
[ 2039.719265]  sda: sda1
[ 2039.733292] sd 2:0:0:0: [sda] Attached SCSI removable disk
[ 2039.733345] sd 2:0:0:0: Attached scsi generic sg0 type 0
[ 2039.746303] sd 3:0:0:0: [sdb] 466907 512-byte hardware sectors (239 MB)
[ 2039.754361] sd 3:0:0:0: [sdb] Write Protect is off
[ 2039.754369] sd 3:0:0:0: [sdb] Mode Sense: 00 6a 00 00
[ 2039.754372] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 2039.766372] sd 3:0:0:0: [sdb] 466907 512-byte hardware sectors (239 MB)
[ 2039.774343] sd 3:0:0:0: [sdb] Write Protect is off
[ 2039.774351] sd 3:0:0:0: [sdb] Mode Sense: 00 6a 00 00
[ 2039.774354] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 2039.774359]  sdb: sdb1
[ 2039.790247]  sdb: p1 exceeds device capacity
[ 2039.792716] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 2039.792774] sd 3:0:0:0: Attached scsi generic sg1 type 0
[ 2040.920560] attempt to access beyond end of device
[ 2040.920569] sdb: rw=0, want=466942, limit=466907
[ 2040.920573] Buffer I/O error on device sdb1, logical block 466904
[ 2040.921208] attempt to access beyond end of device
[ 2040.921212] sdb: rw=0, want=466943, limit=466907
[ 2040.921214] Buffer I/O error on device sdb1, logical block 466905
[ 2040.921756] attempt to access beyond end of device
[ 2040.921759] sdb: rw=0, want=466944, limit=466907
[ 2040.921762] Buffer I/O error on device sdb1, logical block 466906
[ 2040.922281] attempt to access beyond end of device
[ 2040.922285] sdb: rw=0, want=466942, limit=466907
[ 2040.922287] Buffer I/O error on device sdb1, logical block 466904
[ 2040.922837] attempt to access beyond end of device
[ 2040.922841] sdb: rw=0, want=466943, limit=466907
[ 2040.922843] Buffer I/O error on device sdb1, logical block 466905
[ 2040.923328] attempt to access beyond end of device
[ 2040.923332] sdb: rw=0, want=466944, limit=466907
[ 2040.923335] Buffer I/O error on device sdb1, logical block 466906
[ 2040.923859] attempt to access beyond end of device
[ 2040.923863] sdb: rw=0, want=466942, limit=466907
[ 2040.923865] Buffer I/O error on device sdb1, logical block 466904
[ 2040.924375] attempt to access beyond end of device
[ 2040.924379] sdb: rw=0, want=466943, limit=466907
[ 2040.924382] Buffer I/O error on device sdb1, logical block 466905
[ 2040.924988] attempt to access beyond end of device
[ 2040.924992] sdb: rw=0, want=466944, limit=466907
[ 2040.924994] Buffer I/O error on device sdb1, logical block 466906
[ 2040.925537] attempt to access beyond end of device
[ 2040.925541] sdb: rw=0, want=466942, limit=466907
[ 2040.925544] Buffer I/O error on device sdb1, logical block 466904
[ 2040.926073] attempt to access beyond end of device
[ 2040.926077] sdb: rw=0, want=466943, limit=466907
[ 2040.926417] attempt to access beyond end of device
[ 2040.926421] sdb: rw=0, want=466944, limit=466907
[ 2040.926774] attempt to access beyond end of device
[ 2040.926778] sdb: rw=0, want=466942, limit=466907
[ 2040.927121] attempt to access beyond end of device
[ 2040.927125] sdb: rw=0, want=466943, limit=466907
[ 2040.927490] attempt to access beyond end of device
[ 2040.927493] sdb: rw=0, want=466944, limit=466907
[ 2040.927833] attempt to access beyond end of device
[ 2040.927837] sdb: rw=0, want=466942, limit=466907
[ 2040.928202] attempt to access beyond end of device
[ 2040.928206] sdb: rw=0, want=466943, limit=466907
[ 2040.928672] attempt to access beyond end of device
[ 2040.928676] sdb: rw=0, want=466944, limit=466907
[ 2040.929037] attempt to access beyond end of device
[ 2040.929041] sdb: rw=0, want=466942, limit=466907
[ 2040.929389] attempt to access beyond end of device
[ 2040.929393] sdb: rw=0, want=466943, limit=466907
[ 2040.929884] attempt to access beyond end of device
[ 2040.929889] sdb: rw=0, want=466944, limit=466907
[ 2040.978513] attempt to access beyond end of device
[ 2040.978522] sdb: rw=0, want=466926, limit=466907
[ 2040.978982] attempt to access beyond end of device
[ 2040.978986] sdb: rw=0, want=466927, limit=466907
[ 2040.979320] attempt to access beyond end of device
[ 2040.979324] sdb: rw=0, want=466928, limit=466907
[ 2040.979667] attempt to access beyond end of device
[ 2040.979671] sdb: rw=0, want=466929, limit=466907
[ 2040.980040] attempt to access beyond end of device
[ 2040.980044] sdb: rw=0, want=466930, limit=466907
[ 2040.980379] attempt to access beyond end of device
[ 2040.980382] sdb: rw=0, want=466931, limit=466907
[ 2040.980743] attempt to access beyond end of device
[ 2040.980747] sdb: rw=0, want=466932, limit=466907
[ 2040.981080] attempt to access beyond end of device
[ 2040.981084] sdb: rw=0, want=466933, limit=466907
[ 2040.981453] attempt to access beyond end of device
[ 2040.981457] sdb: rw=0, want=466934, limit=466907
[ 2040.981932] attempt to access beyond end of device
[ 2040.981935] sdb: rw=0, want=466935, limit=466907
[ 2040.982282] attempt to access beyond end of device
[ 2040.982286] sdb: rw=0, want=466936, limit=466907
[ 2040.982634] attempt to access beyond end of device
[ 2040.982638] sdb: rw=0, want=466937, limit=466907
[ 2040.983009] attempt to access beyond end of device
[ 2040.983013] sdb: rw=0, want=466938, limit=466907
[ 2040.983361] attempt to access beyond end of device
[ 2040.983365] sdb: rw=0, want=466939, limit=466907
[ 2040.983719] attempt to access beyond end of device
[ 2040.983723] sdb: rw=0, want=466940, limit=466907
[ 2040.984070] attempt to access beyond end of device
[ 2040.984074] sdb: rw=0, want=466941, limit=466907
[ 2040.984444] attempt to access beyond end of device
[ 2040.984447] sdb: rw=0, want=466942, limit=466907
[ 2040.984796] attempt to access beyond end of device
[ 2040.984799] sdb: rw=0, want=466943, limit=466907
[ 2040.985147] attempt to access beyond end of device
[ 2040.985151] sdb: rw=0, want=466944, limit=466907
[ 2040.985524] attempt to access beyond end of device
[ 2040.985528] sdb: rw=0, want=466942, limit=466907
[ 2040.986033] attempt to access beyond end of device
[ 2040.986037] sdb: rw=0, want=466943, limit=466907
[ 2040.986388] attempt to access beyond end of device
[ 2040.986392] sdb: rw=0, want=466944, limit=466907
[ 2041.405107] attempt to access beyond end of device
[ 2041.405117] sdb: rw=0, want=466942, limit=466907
[ 2041.405480] attempt to access beyond end of device
[ 2041.405484] sdb: rw=0, want=466943, limit=466907
[ 2041.405626] attempt to access beyond end of device
[ 2041.405629] sdb: rw=0, want=466944, limit=466907
[ 2041.405769] attempt to access beyond end of device
[ 2041.405772] sdb: rw=0, want=466942, limit=466907
[ 2041.405895] attempt to access beyond end of device
[ 2041.405898] sdb: rw=0, want=466943, limit=466907
[ 2041.406035] attempt to access beyond end of device
[ 2041.406038] sdb: rw=0, want=466944, limit=466907
[ 2041.406193] attempt to access beyond end of device
[ 2041.406196] sdb: rw=0, want=466942, limit=466907
[ 2041.406337] attempt to access beyond end of device
[ 2041.406339] sdb: rw=0, want=466943, limit=466907
[ 2041.406480] attempt to access beyond end of device
[ 2041.406482] sdb: rw=0, want=466944, limit=466907
[ 2041.406627] attempt to access beyond end of device
[ 2041.406630] sdb: rw=0, want=466942, limit=466907
[ 2041.406770] attempt to access beyond end of device
[ 2041.406773] sdb: rw=0, want=466943, limit=466907
[ 2041.406912] attempt to access beyond end of device
[ 2041.406915] sdb: rw=0, want=466944, limit=466907
[ 2041.407059] attempt to access beyond end of device
[ 2041.407062] sdb: rw=0, want=466942, limit=466907
[ 2041.407202] attempt to access beyond end of device
[ 2041.407205] sdb: rw=0, want=466943, limit=466907
[ 2041.407344] attempt to access beyond end of device
[ 2041.407347] sdb: rw=0, want=466944, limit=466907
[ 2041.407491] attempt to access beyond end of device
[ 2041.407494] sdb: rw=0, want=466942, limit=466907
[ 2041.407634] attempt to access beyond end of device
[ 2041.407637] sdb: rw=0, want=466943, limit=466907
[ 2041.407776] attempt to access beyond end of device
[ 2041.407779] sdb: rw=0, want=466944, limit=466907
[ 2041.407923] attempt to access beyond end of device
[ 2041.407926] sdb: rw=0, want=466942, limit=466907
[ 2041.408065] attempt to access beyond end of device
[ 2041.408068] sdb: rw=0, want=466943, limit=466907
[ 2041.408208] attempt to access beyond end of device
[ 2041.408211] sdb: rw=0, want=466944, limit=466907
[ 2041.443192] attempt to access beyond end of device
[ 2041.443202] sdb: rw=0, want=466926, limit=466907
[ 2041.443359] attempt to access beyond end of device
[ 2041.443362] sdb: rw=0, want=466927, limit=466907
[ 2041.443504] attempt to access beyond end of device
[ 2041.443506] sdb: rw=0, want=466928, limit=466907
[ 2041.443647] attempt to access beyond end of device
[ 2041.443649] sdb: rw=0, want=466929, limit=466907
[ 2041.443791] attempt to access beyond end of device
[ 2041.443793] sdb: rw=0, want=466930, limit=466907
[ 2041.443934] attempt to access beyond end of device
[ 2041.443936] sdb: rw=0, want=466931, limit=466907
[ 2041.444077] attempt to access beyond end of device
[ 2041.444080] sdb: rw=0, want=466932, limit=466907
[ 2041.444225] attempt to access beyond end of device
[ 2041.444228] sdb: rw=0, want=466933, limit=466907
[ 2041.444378] attempt to access beyond end of device
[ 2041.444381] sdb: rw=0, want=466934, limit=466907
[ 2041.444629] attempt to access beyond end of device
[ 2041.444632] sdb: rw=0, want=466935, limit=466907
[ 2041.444774] attempt to access beyond end of device
[ 2041.444776] sdb: rw=0, want=466936, limit=466907
[ 2041.444917] attempt to access beyond end of device
[ 2041.444920] sdb: rw=0, want=466937, limit=466907
[ 2041.445062] attempt to access beyond end of device
[ 2041.445064] sdb: rw=0, want=466938, limit=466907
[ 2041.445205] attempt to access beyond end of device
[ 2041.445207] sdb: rw=0, want=466939, limit=466907
[ 2041.445356] attempt to access beyond end of device
[ 2041.445359] sdb: rw=0, want=466940, limit=466907
[ 2041.445501] attempt to access beyond end of device
[ 2041.445504] sdb: rw=0, want=466941, limit=466907
[ 2041.445654] attempt to access beyond end of device
[ 2041.445657] sdb: rw=0, want=466942, limit=466907
[ 2041.445799] attempt to access beyond end of device
[ 2041.445802] sdb: rw=0, want=466943, limit=466907
[ 2041.445942] attempt to access beyond end of device
[ 2041.445945] sdb: rw=0, want=466944, limit=466907
[ 2041.446093] attempt to access beyond end of device
[ 2041.446095] sdb: rw=0, want=466942, limit=466907
[ 2041.446237] attempt to access beyond end of device
[ 2041.446240] sdb: rw=0, want=466943, limit=466907
[ 2041.446380] attempt to access beyond end of device
[ 2041.446383] sdb: rw=0, want=466944, limit=466907

```

---

### Post by sciurus on 2008-07-23
Do you know if these messages occurred before? Are you sure it's not working, but very slowly? Any information you can provide might be helpful for [this bug report]("https://bugs.launchpad.net/ubuntu/+bug/199580").

---

