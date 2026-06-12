---
title: "USB Hard drive randomly unmounting and remounting"
date: 2007-07-04
forum: General Help
---

### Post by ButteBlues on 2007-07-04
I have a new external HDD. I formatted it to ext3, and moved my music over.

Now, however, it will randomly start unmounting and remounting.

Here's what dmesg says:

```
[ 3769.264000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 3769.264000] : Add. Sense: Logical unit not ready, initializing command required
[ 3769.264000] end_request: I/O error, dev sdb, sector 12375
[ 3769.264000] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
[ 3769.276000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 3769.276000] : Add. Sense: Logical unit not ready, initializing command required
[ 3769.276000] end_request: I/O error, dev sdb, sector 63
[ 3769.276000] Buffer I/O error on device sdb1, logical block 0
[ 3769.276000] lost page write due to I/O error on sdb1
[ 3780.976000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 3780.976000] : Add. Sense: Logical unit not ready, initializing command required
[ 3780.976000] end_request: I/O error, dev sdb, sector 12375
[ 3780.976000] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
[ 3827.720000] kjournald starting.  Commit interval 5 seconds
[ 3827.720000] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
[ 3827.728000] EXT3 FS on sdb1, internal journal
[ 3827.728000] EXT3-fs: mounted filesystem with ordered data mode.
[ 5092.960000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 5092.960000] : Add. Sense: Logical unit not ready, initializing command required
[ 5092.960000] end_request: I/O error, dev sdb, sector 319815759
[ 5092.960000] EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read inode block - inode=19988481, block=39976962
[ 5092.972000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 5092.972000] : Add. Sense: Logical unit not ready, initializing command required
[ 5092.972000] end_request: I/O error, dev sdb, sector 63
[ 5092.972000] Buffer I/O error on device sdb1, logical block 0
[ 5092.972000] lost page write due to I/O error on sdb1
[ 5341.844000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 5341.844000] : Add. Sense: Logical unit not ready, initializing command required
[ 5341.844000] end_request: I/O error, dev sdb, sector 12519
[ 5341.844000] journal_bmap: journal block not found at offset 12 on sdb1
[ 5341.844000] Aborting journal on device sdb1.
[ 5348.080000] journal commit I/O error
[ 5352.280000] kjournald starting.  Commit interval 5 seconds
[ 5352.280000] EXT3-fs warning (device sdb1): ext3_clear_journal_err: Filesystem error recorded from previous mount: IO failure
[ 5352.280000] EXT3-fs warning (device sdb1): ext3_clear_journal_err: Marking fs in need of filesystem check.
[ 5352.288000] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
[ 5352.288000] EXT3 FS on sdb1, internal journal
[ 5352.288000] EXT3-fs: mounted filesystem with ordered data mode.
[17906.596000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[17906.596000] : Add. Sense: Logical unit not ready, initializing command required
[17906.596000] end_request: I/O error, dev sdb, sector 272446015
[17906.600000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[17906.600000] : Add. Sense: Logical unit not ready, initializing command required
[17906.600000] end_request: I/O error, dev sdb, sector 272446255
[17908.004000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[17908.004000] : Add. Sense: Logical unit not ready, initializing command required
[17908.004000] end_request: I/O error, dev sdb, sector 58855
[17909.444000] Aborting journal on device sdb1.
[17909.468000] ext3_abort called.
[17909.468000] EXT3-fs error (device sdb1): ext3_journal_start_sb: Detected aborted journal
[17909.468000] Remounting filesystem read-only
[19992.196000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[19992.196000] : Add. Sense: Logical unit not ready, initializing command required
[19992.196000] end_request: I/O error, dev sdb, sector 273665015
[19992.200000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[19992.200000] : Add. Sense: Logical unit not ready, initializing command required
[19992.200000] end_request: I/O error, dev sdb, sector 273665255
[20000.404000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[20000.404000] : Add. Sense: Logical unit not ready, initializing command required
[20000.404000] end_request: I/O error, dev sdb, sector 273665271
[24115.568000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[24115.568000] : Add. Sense: Logical unit not ready, initializing command required
[24115.568000] end_request: I/O error, dev sdb, sector 302268543
[24115.568000] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #18890758 offset 0
[24119.924000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[24119.924000] : Add. Sense: Logical unit not ready, initializing command required
[24119.924000] end_request: I/O error, dev sdb, sector 302268543
[24119.924000] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #18890758 offset 0
[24161.532000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[24161.532000] : Add. Sense: Logical unit not ready, initializing command required
[24161.532000] end_request: I/O error, dev sdb, sector 12423
[24161.532000] Buffer I/O error on device sdb1, logical block 1545
[24161.532000] lost page write due to I/O error on sdb1
[24175.584000] kjournald starting.  Commit interval 5 seconds
[24175.584000] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
[24175.584000] EXT3 FS on sdb1, internal journal
[24175.584000] EXT3-fs: recovery complete.
[24175.588000] EXT3-fs: mounted filesystem with ordered data mode.
[41748.688000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[41748.688000] : Add. Sense: Logical unit not ready, initializing command required
[41748.688000] end_request: I/O error, dev sdb, sector 12375
[41748.688000] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
[41748.700000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[41748.700000] : Add. Sense: Logical unit not ready, initializing command required
[41748.700000] end_request: I/O error, dev sdb, sector 63
[41748.700000] Buffer I/O error on device sdb1, logical block 0
[41748.700000] lost page write due to I/O error on sdb1
[50092.556000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[50092.556000] : Add. Sense: Logical unit not ready, initializing command required
[50092.556000] end_request: I/O error, dev sdb, sector 271253567
[50092.556000] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #16941057 offset 0
[50092.564000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[50092.564000] : Add. Sense: Logical unit not ready, initializing command required
[50092.564000] end_request: I/O error, dev sdb, sector 63
[50092.564000] Buffer I/O error on device sdb1, logical block 0
[50092.564000] lost page write due to I/O error on sdb1
[50263.024000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[50263.024000] : Add. Sense: Logical unit not ready, initializing command required
[50263.024000] end_request: I/O error, dev sdb, sector 12375
[50263.072000] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
[50263.076000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[50263.076000] : Add. Sense: Logical unit not ready, initializing command required
[50263.076000] end_request: I/O error, dev sdb, sector 63
[50263.076000] Buffer I/O error on device sdb1, logical block 0
[50263.076000] lost page write due to I/O error on sdb1
[50263.124000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[50263.124000] : Add. Sense: Logical unit not ready, initializing command required
[50263.124000] end_request: I/O error, dev sdb, sector 12375
[50263.176000] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
```

And ideas how to fix this?

---

### Post by ButteBlues on 2007-07-07
I've formatted the disk to Ext3 since then, and I still get these errors.

Since so many posts over the forum have the same issue on other **perfectly good** hard drives, I'm just going to assume it's an ext3 problem and change to JFS or Reiser.

---

### Post by toran on 2007-09-08
Does anyone have a solution for this? I'm having the same problem.

---

### Post by toran on 2007-09-10
anyone?

---

### Post by dcstar on 2007-09-11
> **toran said:**
> Does anyone have a solution for this? I'm having the same problem.

If the drive is solely powered off the USB connection, I would remove any other items from that particular USB hub to see if it has adequate current to power the disk.

I have had issues with USB devices overloading the connection and "sort of" working, but only working correctly when it was the only device on the hub.

---

### Post by toran on 2007-09-11
the device plugs into an outlet to get power, I don't believe that is the problem.

---

### Post by infinity0 on 2007-09-16
ButteBlues, has your problem stopped after switching filesystems? I've got what looks to be a very similar problem (including some of the same errors in dmesg), except mine remounts as read-only due to (i'm guessing) it being an encrypted partition.

---

### Post by ButteBlues on 2007-09-16
This has not been fixed.

When it remounts as ro (or in some cases, not readable at all), I have to manually umount, fsck, then remount.

---

### Post by infinity0 on 2007-09-16
hmm yeah same here. which filesystems have you tried reformatting to?

---

### Post by nowshining on 2007-09-16
ButteBlues is this on Gutsy Gibbon, if so it would be best to go to launchpad do a search for a similiar bug report and if not report a bug there..

---

### Post by ButteBlues on 2007-09-16
> **nowshining said:**
> ButteBlues is this on Gutsy Gibbon, if so it would be best to go to launchpad do a search for a similiar bug report and if not report a bug there..
This behavior has been around since about Edgy.

As far as I know, there's been no resolution to it - partly because no one's really sure where the problem lies.


I've tried ext3, reiserfs, jfs, xfs, and fat32.

---

### Post by nowshining on 2007-09-16
strange As i have an external NTFS drive and on my side everything is working fine.

edit: n/m I get external somehow mixed up with extra internal drive..

---

### Post by Ramzi on 2007-09-19
I too can confirm this behaviour, an external disk formatted as Ext3 just freaks out when i plug it in:

Here is my dmesg output after a couple of power cycles:

```
[ 2851.697223] usb 3-5: new high speed USB device using ehci_hcd and address 4
[ 2851.824000] usb 3-5: configuration #1 chosen from 1 choice
[ 2852.019611] usbcore: registered new interface driver libusual
[ 2852.036455] Initializing USB Mass Storage driver...
[ 2852.036720] scsi1 : SCSI emulation for USB Mass Storage devices
[ 2852.036924] usbcore: registered new interface driver usb-storage
[ 2852.037072] USB Mass Storage support registered.
[ 2852.037296] usb-storage: device found at 4
[ 2852.037422] usb-storage: waiting for device to settle before scanning
[ 2857.035385] usb-storage: device scan complete
[ 2857.037375] scsi 1:0:0:0: Direct-Access     ST325082 0A               0811 PQ: 0 ANSI: 0
[ 2857.038813] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[ 2857.040091] sd 1:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2857.040094] sd 1:0:0:0: [sdb] Assuming drive cache: write through
[ 2857.041177] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[ 2857.042438] sd 1:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2857.042443] sd 1:0:0:0: [sdb] Assuming drive cache: write through
[ 2857.042447]  sdb: sdb1 < sdb5 >
[ 2857.063755] sd 1:0:0:0: [sdb] Attached SCSI disk
[ 2857.063794] sd 1:0:0:0: Attached scsi generic sg1 type 0
[ 2857.524942] kjournald starting.  Commit interval 5 seconds
[ 2857.532568] EXT3 FS on sdb5, internal journal
[ 2857.532579] EXT3-fs: mounted filesystem with ordered data mode.
[ 2862.848955] usb 3-5: USB disconnect, address 4
[ 2862.848981] sd 1:0:0:0: [sdb] Result: hostbyte=0x07 driverbyte=0x00
[ 2862.848990] end_request: I/O error, dev sdb, sector 12606
[ 2862.848997] Buffer I/O error on device sdb5, logical block 1560
[ 2862.849003] lost page write due to I/O error on sdb5
[ 2862.849290] sd 1:0:0:0: [sdb] Result: hostbyte=0x07 driverbyte=0x00
[ 2862.849297] end_request: I/O error, dev sdb, sector 12614
[ 2862.849864] sd 1:0:0:0: [sdb] Result: hostbyte=0x07 driverbyte=0x00
[ 2862.849872] end_request: I/O error, dev sdb, sector 12630
[ 2862.849877] Buffer I/O error on device sdb5, logical block 1563
[ 2862.849882] lost page write due to I/O error on sdb5
[ 2862.849945] Aborting journal on device sdb5.
[ 2862.850800] Buffer I/O error on device sdb5, logical block 1042
[ 2862.850806] lost page write due to I/O error on sdb5
[ 2862.955322] WARNING: at fs/buffer.c:1154 mark_buffer_dirty()
[ 2862.955340]  [<c019f1f9>] mark_buffer_dirty+0x79/0x90
[ 2862.955355]  [<c01dc00f>] journal_update_superblock+0x6f/0xd0
[ 2862.955366]  [<c01dc873>] journal_destroy+0x1c3/0x210
[ 2862.955374]  [<c019135e>] destroy_inode+0x2e/0x50
[ 2862.955384]  [<c013e320>] autoremove_wake_function+0x0/0x50
[ 2862.955395]  [<c01ced72>] ext3_put_super+0x22/0x1f0
[ 2862.955404]  [<c0191f63>] invalidate_inodes+0xc3/0xd0
[ 2862.955413]  [<c017f1a5>] generic_shutdown_super+0x55/0xf0
[ 2862.955423]  [<c017f24c>] kill_block_super+0xc/0x20
[ 2862.955431]  [<c017f31e>] deactivate_super+0x6e/0x90
[ 2862.955439]  [<c019441a>] sys_umount+0x4a/0x270
[ 2862.955449]  [<c016ba99>] remove_vma+0x39/0x50
[ 2862.955460]  [<c01043fe>] sysenter_past_esp+0x6b/0xa1
[ 2862.955471]  =======================
[ 2862.955491] scsi 1:0:0:0: rejecting I/O to dead device
[ 2862.955500] Buffer I/O error on device sdb5, logical block 1560
[ 2862.955505] lost page write due to I/O error on sdb5
[ 2862.955730] scsi 1:0:0:0: rejecting I/O to dead device
[ 2862.955735] Buffer I/O error on device sdb5, logical block 0
[ 2862.955740] lost page write due to I/O error on sdb5
[ 2862.959692] usb 3-5: new high speed USB device using ehci_hcd and address 5
[ 2863.061921] usb 3-5: device descriptor read/64, error -71
[ 2863.264590] usb 3-5: device descriptor read/64, error -71
[ 2863.467756] usb 3-5: new high speed USB device using ehci_hcd and address 6
[ 2863.570730] usb 3-5: device descriptor read/64, error -71
[ 2863.773389] usb 3-5: device descriptor read/64, error -71
[ 2863.976622] usb 3-5: new high speed USB device using ehci_hcd and address 7
[ 2864.378211] usb 3-5: device not accepting address 7, error -71
[ 2864.480176] usb 3-5: new high speed USB device using ehci_hcd and address 8
[ 2864.882015] usb 3-5: device not accepting address 8, error -71
[ 2865.514682] usb 3-5: new high speed USB device using ehci_hcd and address 9
[ 2865.616916] usb 3-5: device descriptor read/64, error -71
[ 2865.819790] usb 3-5: device descriptor read/64, error -71
[ 2866.022498] usb 3-5: new high speed USB device using ehci_hcd and address 10
[ 2866.128958] usb 3-5: device descriptor read/64, error -71
[ 2866.331611] usb 3-5: device descriptor read/64, error -71
[ 2866.534354] usb 3-5: new high speed USB device using ehci_hcd and address 11
[ 2866.936198] usb 3-5: device not accepting address 11, error -71
[ 2867.038104] usb 3-5: new high speed USB device using ehci_hcd and address 12
[ 2867.439986] usb 3-5: device not accepting address 12, error -71
[ 2916.570313] usb 3-5: new high speed USB device using ehci_hcd and address 13
[ 2916.699520] usb 3-5: configuration #1 chosen from 1 choice
[ 2916.700110] scsi2 : SCSI emulation for USB Mass Storage devices
[ 2916.700766] usb-storage: device found at 13
[ 2916.701075] usb-storage: waiting for device to settle before scanning
[ 2921.699835] usb-storage: device scan complete
[ 2921.701731] scsi 2:0:0:0: Direct-Access     ST325082 0A               0811 PQ: 0 ANSI: 0
[ 2921.704334] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[ 2921.705715] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2921.705723] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 2921.706843] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[ 2921.708308] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2921.708316] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 2921.708321]  sdb: sdb1 < sdb5 >
[ 2921.726167] sd 2:0:0:0: [sdb] Attached SCSI disk
[ 2921.726368] sd 2:0:0:0: Attached scsi generic sg1 type 0
[ 2922.020990] kjournald starting.  Commit interval 5 seconds
[ 2922.020998] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[ 2922.028752] EXT3 FS on sdb5, internal journal
[ 2922.028755] EXT3-fs: recovery complete.
[ 2922.028758] EXT3-fs: mounted filesystem with ordered data mode.
[ 2925.400924] usb 3-5: USB disconnect, address 13
[ 2925.402502] Buffer I/O error on device sdb5, logical block 1560
[ 2925.402513] lost page write due to I/O error on sdb5
[ 2925.402996] Buffer I/O error on device sdb5, logical block 1563
[ 2925.403004] lost page write due to I/O error on sdb5
[ 2925.403425] Aborting journal on device sdb5.
[ 2925.403600] journal commit I/O error
[ 2925.403642] Buffer I/O error on device sdb5, logical block 1042
[ 2925.403647] lost page write due to I/O error on sdb5
[ 2925.422297] scsi 2:0:0:0: rejecting I/O to dead device
[ 2925.422305] Buffer I/O error on device sdb5, logical block 1560
[ 2925.422307] lost page write due to I/O error on sdb5
[ 2925.422675] scsi 2:0:0:0: rejecting I/O to dead device
[ 2925.422678] Buffer I/O error on device sdb5, logical block 0
[ 2925.422680] lost page write due to I/O error on sdb5
[ 2925.513568] usb 3-5: new high speed USB device using ehci_hcd and address 14
[ 2925.615717] usb 3-5: device descriptor read/64, error -71
[ 2925.818837] usb 3-5: device descriptor read/64, error -71
[ 2926.021538] usb 3-5: new high speed USB device using ehci_hcd and address 15
[ 2926.123473] usb 3-5: device descriptor read/64, error -71
[ 2926.326402] usb 3-5: device descriptor read/64, error -71
[ 2926.530346] usb 3-5: new high speed USB device using ehci_hcd and address 16
[ 2926.932406] usb 3-5: device not accepting address 16, error -71
[ 2927.034183] usb 3-5: new high speed USB device using ehci_hcd and address 17
[ 2927.435952] usb 3-5: device not accepting address 17, error -71
[ 2955.480770] usb 3-5: new high speed USB device using ehci_hcd and address 18
[ 2955.582708] usb 3-5: device descriptor read/64, error -71
[ 3074.777094] usb 3-5: new high speed USB device using ehci_hcd and address 19
[ 3074.904055] usb 3-5: configuration #1 chosen from 1 choice
[ 3074.904534] scsi3 : SCSI emulation for USB Mass Storage devices
[ 3074.905072] usb-storage: device found at 19
[ 3074.905284] usb-storage: waiting for device to settle before scanning
[ 3079.903465] usb-storage: device scan complete
[ 3079.905768] scsi 3:0:0:0: Direct-Access     ST325082 0A               0811 PQ: 0 ANSI: 0
[ 3079.907717] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[ 3079.908970] sd 3:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3079.908993] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3079.909949] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[ 3079.911258] sd 3:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3079.911263] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3079.911266]  sdb: sdb1 < sdb5 >
[ 3079.930670] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 3079.931047] sd 3:0:0:0: Attached scsi generic sg1 type 0
[ 3080.242050] kjournald starting.  Commit interval 5 seconds
[ 3080.242064] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[ 3080.250575] EXT3 FS on sdb5, internal journal
[ 3080.250581] EXT3-fs: recovery complete.
[ 3080.250584] EXT3-fs: mounted filesystem with ordered data mode.
[ 3135.113114] usb 3-5: USB disconnect, address 19
[ 3135.115305] journal_bmap: journal block not found at offset 12 on sdb5
[ 3135.115309] Aborting journal on device sdb5.
[ 3135.115316] Buffer I/O error on device sdb5, logical block 1560
[ 3135.115318] lost page write due to I/O error on sdb5
[ 3135.115388] journal commit I/O error
[ 3135.115416] Buffer I/O error on device sdb5, logical block 26148866
[ 3135.115418] lost page write due to I/O error on sdb5
[ 3135.115421] Buffer I/O error on device sdb5, logical block 26148867
[ 3135.115423] lost page write due to I/O error on sdb5
[ 3135.115425] Buffer I/O error on device sdb5, logical block 26148868
[ 3135.115427] lost page write due to I/O error on sdb5
[ 3135.115429] Buffer I/O error on device sdb5, logical block 26148869
[ 3135.115431] lost page write due to I/O error on sdb5
[ 3135.115434] Buffer I/O error on device sdb5, logical block 26148873
[ 3135.115435] lost page write due to I/O error on sdb5
[ 3135.115438] Buffer I/O error on device sdb5, logical block 26148884
[ 3135.115440] lost page write due to I/O error on sdb5
[ 3135.115443] Buffer I/O error on device sdb5, logical block 1042
[ 3135.115444] lost page write due to I/O error on sdb5
[ 3135.115455] Buffer I/O error on device sdb5, logical block 26148890
[ 3135.115457] lost page write due to I/O error on sdb5
[ 3135.115459] Buffer I/O error on device sdb5, logical block 26148901
[ 3135.115461] lost page write due to I/O error on sdb5
[ 3135.132918] scsi 3:0:0:0: rejecting I/O to dead device
[ 3135.133105] scsi 3:0:0:0: rejecting I/O to dead device
[ 3135.257131] usb 3-5: new high speed USB device using ehci_hcd and address 20
[ 3135.358915] usb 3-5: device descriptor read/64, error -71
[ 3135.562030] usb 3-5: device descriptor read/64, error -71
[ 3135.764738] usb 3-5: new high speed USB device using ehci_hcd and address 21
[ 3135.866738] usb 3-5: device descriptor read/64, error -71
[ 3136.071656] usb 3-5: device descriptor read/64, error -71
[ 3136.274578] usb 3-5: new high speed USB device using ehci_hcd and address 22
[ 3136.676408] usb 3-5: device not accepting address 22, error -71
[ 3136.778326] usb 3-5: new high speed USB device using ehci_hcd and address 23
[ 3137.180210] usb 3-5: device not accepting address 23, error -71
[ 3165.391893] usb 3-5: new high speed USB device using ehci_hcd and address 24
[ 3165.508077] usb 3-5: device descriptor read/64, error -71
[ 3165.718810] usb 3-5: device descriptor read/64, error -71
[ 3165.921662] usb 3-5: new high speed USB device using ehci_hcd and address 25
[ 3166.023861] usb 3-5: device descriptor read/64, error -71
[ 3166.226545] usb 3-5: device descriptor read/64, error -71
[ 3166.429700] usb 3-5: new high speed USB device using ehci_hcd and address 26
[ 3166.831274] usb 3-5: device not accepting address 26, error -71
[ 3166.933271] usb 3-5: new high speed USB device using ehci_hcd and address 27
[ 3167.335159] usb 3-5: device not accepting address 27, error -71
[ 3195.386900] usb 3-5: new high speed USB device using ehci_hcd and address 28
[ 3195.488855] usb 3-5: device descriptor read/64, error -71
[ 3195.691770] usb 3-5: device descriptor read/64, error -71
[ 3195.894940] usb 3-5: new high speed USB device using ehci_hcd and address 29
[ 3195.996667] usb 3-5: device descriptor read/64, error -71
[ 3196.199647] usb 3-5: device descriptor read/64, error -71
[ 3196.402502] usb 3-5: new high speed USB device using ehci_hcd and address 30
[ 3196.804387] usb 3-5: device not accepting address 30, error -71
[ 3196.906598] usb 3-5: new high speed USB device using ehci_hcd and address 31
[ 3197.308119] usb 3-5: device not accepting address 31, error -71
[ 3412.601347] ehci_hcd 0000:00:1d.7: remove, state 4
[ 3412.601361] usb usb3: USB disconnect, address 1
[ 3412.620349] ehci_hcd 0000:00:1d.7: USB bus 3 deregistered
[ 3412.620627] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[ 3412.620816] ehci_hcd 0000:00:1a.7: remove, state 4
[ 3412.620948] usb usb2: USB disconnect, address 1
[ 3412.637338] ehci_hcd 0000:00:1a.7: USB bus 2 deregistered
[ 3412.637387] ACPI: PCI interrupt for device 0000:00:1a.7 disabled
[ 3428.980349] usb 7-1: new full speed USB device using uhci_hcd and address 2
[ 3429.137926] usb 7-1: configuration #1 chosen from 1 choice
[ 3429.141003] scsi4 : SCSI emulation for USB Mass Storage devices
[ 3429.142156] usb-storage: device found at 2
[ 3429.142471] usb-storage: waiting for device to settle before scanning
[ 3434.142061] usb-storage: device scan complete
[ 3434.145016] scsi 4:0:0:0: Direct-Access     ST325082 0A               0811 PQ: 0 ANSI: 0
[ 3434.151021] sd 4:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[ 3434.158007] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3434.158016] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3434.163030] sd 4:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[ 3434.169961] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3434.169969] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3434.169974]  sdb: sdb1 < sdb5 >
[ 3434.199310] sd 4:0:0:0: [sdb] Attached SCSI disk
[ 3434.199854] sd 4:0:0:0: Attached scsi generic sg1 type 0
[ 3435.761130] kjournald starting.  Commit interval 5 seconds
[ 3435.761238] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[ 3435.769103] EXT3 FS on sdb5, internal journal
[ 3435.769111] EXT3-fs: recovery complete.
[ 3435.775084] EXT3-fs: mounted filesystem with ordered data mode.
[ 3649.458544] usb 7-1: USB disconnect, address 2
[ 3672.773147] usb 7-1: new full speed USB device using uhci_hcd and address 3
[ 3672.933291] usb 7-1: configuration #1 chosen from 1 choice
[ 3672.935370] scsi5 : SCSI emulation for USB Mass Storage devices
[ 3672.936560] usb-storage: device found at 3
[ 3672.936874] usb-storage: waiting for device to settle before scanning
[ 3677.935422] usb-storage: device scan complete
[ 3677.939409] scsi 5:0:0:0: Direct-Access     ST325082 0A               0811 PQ: 0 ANSI: 0
[ 3677.945334] sd 5:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[ 3677.952307] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3677.952316] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3677.957307] sd 5:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[ 3677.964279] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3677.964285] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3677.964289]  sdb: sdb1 < sdb5 >
[ 3677.988607] sd 5:0:0:0: [sdb] Attached SCSI disk
[ 3677.988686] sd 5:0:0:0: Attached scsi generic sg1 type 0
[ 3679.383690] kjournald starting.  Commit interval 5 seconds
[ 3679.383716] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[ 3679.397529] EXT3 FS on sdb5, internal journal
[ 3679.397541] EXT3-fs: mounted filesystem with ordered data mode.
```

---

### Post by toran on 2007-09-20
How can we bring this to the attention of people who can fix this so that they know it is a problem and needs to be fixed?

---

### Post by spacedcadet27 on 2007-09-23
I'm having the exact same problem and I can't find an answer anywhere. Except my drive is formatted fat32 and also has external power. If you find an answer please message me and if I find one I will be sure to do the same....oh and I also tried it with my dyne:bolic live disk and I get the same output.

---

### Post by toran on 2007-09-24
I asked in IRC about this thread and it was recommended that I return the drive and get a new one.

Does anyone else think that the drives giving these errors are defective?

---

### Post by shamrock_uk on 2007-09-24
> **toran said:**
> How can we bring this to the attention of people who can fix this so that they know it is a problem and needs to be fixed?

You need to report a bug [here](https://launchpad.net/ubuntu/+filebug/+login).

Have you tried plugging the drive into a different computer? Different USB slot? Format as FAT32 - what does Windows make of it? (check event viewer for disk errors)

---

### Post by ButteBlues on 2007-09-24
> **toran said:**
> I asked in IRC about this thread and it was recommended that I return the drive and get a new one.

Does anyone else think that the drives giving these errors are defective?
The drive worked as expected connected to both Windows and OSX.

---

### Post by gwi on 2007-09-26
I am having the same problems with an internal SATA drive. Tried several combinations of harddisks and motherboards, ext3 and ReiserFS. For the past months I've spent more time reinstalling, trying to get my system running, than doing real work on it. It is really starting to piss me off.

Hey Canonical, do you occasionaly read the forums and the bug reports? Looks like hundreds of people are having problems like this. If you want people to turn their back to Ubuntu and switch (back) to Windows you are doing a fine job.:mad:

---

### Post by evarlast on 2007-10-05
I am having the same problem here on fiesty. I am using a Seagate FreeAgent Pro 750G connected via USB to a Dell PowerEdige 750.

[53476.014029] sd 3:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[53476.014038]     Additional sense: Logical unit not ready, initializing command required
[53476.014045] end_request: I/O error, dev sdc, sector 12375
[53476.022142] sd 3:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[53476.022150]     Additional sense: Logical unit not ready, initializing command required
[53476.022156] end_request: I/O error, dev sdc, sector 8279
[53476.022517] EXT3-fs error (device dm-3): ext3_get_inode_loc: unable to read inode block - inode=2, block=1027
[53476.022529] Aborting journal on device dm-3.
[53476.035118] sd 3:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[53476.035125]     Additional sense: Logical unit not ready, initializing command required
[53476.035131] end_request: I/O error, dev sdc, sector 12423
[53476.035137] Buffer I/O error on device dm-3, logical block 1545
[53476.035140] lost page write due to I/O error on dm-3
[53476.035626] Remounting filesystem read-only

I'm considering trying the kernel from gutsy in hopes that this is a usb-storage issue.

---

### Post by evarlast on 2007-10-05
I found more information on this.

Apparently the Seagate FreeAgentPro has some issues:  
[http://thebs413.blogspot.com/2007/06/seagate-free-agent-pro-forgets-esata.html](http://thebs413.blogspot.com/2007/06/seagate-free-agent-pro-forgets-esata.html)


NSLU2 has some good general linux information on external drives : [http://www.nslu2-linux.org/wiki/FAQ/SpinDownUSBHarddisks](http://www.nslu2-linux.org/wiki/FAQ/SpinDownUSBHarddisks)

and FreeAgent specifically:
[http://www.nslu2-linux.org/wiki/FAQ/DealWithAutoSpinDownOnSeagateFreeAgent](http://www.nslu2-linux.org/wiki/FAQ/DealWithAutoSpinDownOnSeagateFreeAgent)


In my case my disk is sdc, so I used sudo and tee to write to the virtual file (the kernel) in /sys...

jrwren@destrier:/$ cat /sys/block/sdc/device/scsi_disk\:3\:0\:0\:0/allow_restart
0
jrwren@destrier:/$ echo 1 | sudo tee /sys/block/sdc/device/scsi_disk\:3\:0\:0\:0/allow_restart
1
jrwren@destrier:/$ cat /sys/block/sdc/device/scsi_disk\:3\:0\:0\:0/allow_restart
1

I hope this helps.

Unfortunately I could not actually stop the drives powerdown mode:

$ sudo apt-get install sdparm
$ sudo sdparm --clear STANDBY /dev/sdc
    /dev/sdc: Seagate   FreeAgent Pro  400A
change_mode_page: failed setting page: Power condition


:(

---

### Post by stedfan on 2007-10-05
Hi, i have a freeagent drive too, i googled and stumbled on this :

[http://alienghic.livejournal.com/382903.html](http://alienghic.livejournal.com/382903.html)

---

### Post by toran on 2007-10-09
> **stedfan said:**
> Hi, i have a freeagent drive too, i googled and stumbled on this :

[http://alienghic.livejournal.com/382903.html](http://alienghic.livejournal.com/382903.html)

is this something you would need to do at every reboot? should it be put in a startup file?

---

### Post by Dan Tull on 2007-12-04
I experienced this problem as well after recently purchasing a 500GB FreeAgent drive.  I managed to resolve it by booting into Windows and using the FreeAgent tools to set the spin down interval to "never" (there's also an option to turn off the drive's lights).

That's obviously not ideal both because it requires a tool that only runs on Windows and because it means the drive never spins down, but for now it's the best option I have.  I'm hoping to find some time to reverse engineer the protocol involved so a Linux side tool for configuring the option is possible, but I'm not sure when that'll happen.  I tried to use a USB sniffer, but it wasn't seeing messages sent ore received at the point when I executed the configuration commands in the tool.

DT

---

