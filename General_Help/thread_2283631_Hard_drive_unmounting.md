---
title: "Hard drive unmounting"
date: 2015-06-23
forum: General Help
---

### Post by Umer_Salman on 2015-06-23
I have /root on an SSD and /home on an HDD, both inside my laptop (Lenovo Thinkpad Twist). 


I originally had all of the Ubuntu install on the SSD, but I ran out of space and had to make the move. 


I did so using the 2nd answer on this page: [http://askubuntu.com/questions/21321/move-home-folder-to-second-drive](http://askubuntu.com/questions/21321/move-home-folder-to-second-drive) (the one by Takkat). 


It seemed to be working fine, but after using it for a while, the HDD unmounts itself and I am unable to use any apps or access my data. This is fixed by a restart, but I'd rather not be restarting every ~hour. 


I ran dmesg before it unmounted and ran it again afterwards and here is the relevant portion of the dmesg. 


```
[  118.150677] thinkpad_ec: thinkpad_ec_read_row: failed requesting row: (0x01:0x00)->0xfffffff0
[  118.150683] thinkpad_ec: initial ec test failed
[  566.848385] ata1: exception Emask 0x50 SAct 0x0 SErr 0x40d0800 action 0xe frozen
[  566.848399] ata1: irq_stat 0x00400040, connection status changed
[  566.848408] ata1: SError: { HostInt PHYRdyChg CommWake 10B8B DevExch }
[  566.848421] ata1: hard resetting link
[  568.019669] ata1: SATA link down (SStatus 0 SControl 300)
[  573.022463] ata1: hard resetting link
[  573.350643] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  573.351837] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[  573.351847] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[  573.351853] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[  573.354301] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[  573.354311] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[  573.354317] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[  573.355498] ata1.00: configured for UDMA/133
[  573.370594] ata1: EH complete
[  579.831347] ata1: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
[  579.831359] ata1: irq_stat 0x00400040, connection status changed
[  579.831366] ata1: SError: { HostInt PHYRdyChg 10B8B DevExch }
[  579.831376] ata1: hard resetting link
[  580.554962] ata1: SATA link down (SStatus 0 SControl 300)
[  585.558098] ata1: hard resetting link
[  587.851546] ata1: SATA link down (SStatus 1 SControl 300)
[  587.851579] ata1: limiting SATA link speed to 1.5 Gbps
[  587.852279] ata1: hard resetting link
[  590.073073] ata1: SATA link down (SStatus 1 SControl 310)
[  590.073091] ata1.00: disabled
[  590.077033] sd 0:0:0:0: rejecting I/O to offline device
[  590.077049] sd 0:0:0:0: [sda] killing request
[  590.077132] sd 0:0:0:0: [sda] FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  590.077145] sd 0:0:0:0: [sda] CDB: 
[  590.077155] Write(10): 2a 00 18 44 89 18 00 00 60 00
[  590.077185] blk_update_request: I/O error, dev sda, sector 407144728
[  590.077628] Aborting journal on device sda1-8.
[  590.077682] sd 0:0:0:0: rejecting I/O to offline device
[  590.077702] JBD2: Error -5 detected when updating journal superblock for sda1-8.
[  590.078001] sd 0:0:0:0: rejecting I/O to offline device
[  590.078027] EXT4-fs error (device sda1): ext4_journal_check_start:56: Detected aborted journal
[  590.078038] EXT4-fs (sda1): Remounting filesystem read-only
[  590.078047] EXT4-fs (sda1): previous I/O error to superblock detected
[  590.078067] sd 0:0:0:0: rejecting I/O to offline device
[  590.089040] ata1: exception Emask 0x10 SAct 0x0 SErr 0x4040000 action 0xe frozen t4
[  590.089051] ata1: irq_stat 0x00000040, connection status changed
[  590.089057] ata1: SError: { CommWake DevExch }
[  590.089068] ata1: hard resetting link
[  591.261776] ata1: SATA link down (SStatus 0 SControl 300)
[  591.277796] ata1: EH complete
[  591.277819] ata1.00: detaching (SCSI 0:0:0:0)
[  591.316119] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  591.316180] sd 0:0:0:0: [sda] Synchronize Cache(10) failed: Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  591.316186] sd 0:0:0:0: [sda] Stopping disk
[  591.316203] sd 0:0:0:0: [sda] Start/Stop Unit failed: Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  591.355849] EXT4-fs warning (device sda1): __ext4_read_dirblock:884: error -5 reading directory block (ino 14681066, block 0)
[  591.355869] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #14422744: comm IndexedDB: reading directory lblock 0
[  591.356032] EXT4-fs error (device sda1): __ext4_get_inode_loc:3771: inode #14423886: block 57672084: comm Chrome_DBThread: unable to read itable block
[  591.356136] EXT4-fs error (device sda1): __ext4_get_inode_loc:3771: inode #14423886: block 57672084: comm Chrome_DBThread: unable to read itable block
[  591.356164] EXT4-fs error (device sda1): __ext4_get_inode_loc:3771: inode #14423886: block 57672084: comm Chrome_DBThread: unable to read itable block
[  591.356322] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  591.432250] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #14417921: comm nautilus: reading directory lblock 0
[  591.432262] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #14942870: comm nautilus: reading directory lblock 0
[  591.444989] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #14942870: comm nautilus: reading directory lblock 0
[  591.469482] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #14417921: comm nautilus: reading directory lblock 0
[  591.469497] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #14417921: comm nautilus: reading directory lblock 0
[  591.469508] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #14417921: comm nautilus: reading directory lblock 0
[  592.893296] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  595.388637] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  595.388715] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  595.394764] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  595.403240] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  595.403338] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  596.524670] EXT4-fs warning (device sda1): __ext4_read_dirblock:884: error -5 reading directory block (ino 14422750, block 0)
[  596.892958] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  596.893119] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  596.894181] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  596.895220] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  597.881910] EXT4-fs error: 7 callbacks suppressed
[  597.881915] EXT4-fs error (device sda1): __ext4_get_inode_loc:3771: inode #14417972: block 57671715: comm BrowserBlocking: unable to read itable block
[  601.089463] EXT4-fs error (device sda1): __ext4_get_inode_loc:3771: inode #14417972: block 57671715: comm BrowserBlocking: unable to read itable block
[  605.422100] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #14420095: comm BrowserBlocking: reading directory lblock 0
[  605.481443] EXT4-fs error (device sda1): __ext4_get_inode_loc:3771: inode #14417972: block 57671715: comm BrowserBlocking: unable to read itable block
[  607.340945] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  611.087139] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #14417921: comm unity-panel-ser: reading directory lblock 0
[  611.269500] EXT4-fs error (device sda1): __ext4_get_inode_loc:3771: inode #14423863: block 57672083: comm BrowserBlocking: unable to read itable block
[  611.269574] EXT4-fs error (device sda1): __ext4_get_inode_loc:3771: inode #14423863: block 57672083: comm BrowserBlocking: unable to read itable block
[  611.269594] EXT4-fs error (device sda1): __ext4_get_inode_loc:3771: inode #14423863: block 57672083: comm BrowserBlocking: unable to read itable block
[  611.269695] EXT4-fs error (device sda1): __ext4_get_inode_loc:3771: inode #14423863: block 57672083: comm BrowserBlocking: unable to read itable block
[  611.269725] EXT4-fs error (device sda1): __ext4_get_inode_loc:3771: inode #14423863: block 57672083: comm BrowserBlocking: unable to read itable block
[  611.269731] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  611.269791] EXT4-fs error (device sda1): __ext4_get_inode_loc:3771: inode #14423863: block 57672083: comm BrowserBlocking: unable to read itable block
[  611.269811] EXT4-fs error (device sda1): __ext4_get_inode_loc:3771: inode #14423863: block 57672083: comm BrowserBlocking: unable to read itable block
[  611.269861] EXT4-fs error (device sda1): __ext4_get_inode_loc:3771: inode #14423863: block 57672083: comm BrowserBlocking: unable to read itable block
[  611.269880] EXT4-fs error (device sda1): __ext4_get_inode_loc:3771: inode #14423863: block 57672083: comm BrowserBlocking: unable to read itable block
[  611.270121] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  613.085488] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  613.204054] EXT4-fs warning (device sda1): __ext4_read_dirblock:884: error -5 reading directory block (ino 14417921, block 0)
[  617.249128] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  617.348399] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  617.348458] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  617.740885] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  617.740932] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  617.741990] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  617.742026] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  617.742047] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  619.659393] EXT4-fs error: 16 callbacks suppressed
[  619.659399] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #14420095: comm BrowserBlocking: reading directory lblock 0
[  621.119377] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  621.121685] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  621.448655] EXT4-fs error (device sda1): ext4_wait_block_bitmap:494: comm Chrome_CacheThr: Cannot read block bitmap - block_group = 246, block_bitmap = 7864326
[  621.448661] EXT4-fs error (device sda1): ext4_discard_preallocations:4004: comm Chrome_CacheThr: Error reading block bitmap for 246
[  621.448677] EXT4-fs error (device sda1): ext4_wait_block_bitmap:494: comm Chrome_CacheThr: Cannot read block bitmap - block_group = 17, block_bitmap = 524289
[  621.448679] EXT4-fs error (device sda1): ext4_discard_preallocations:4004: comm Chrome_CacheThr: Error reading block bitmap for 17
[  621.448736] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #14811503: comm Chrome_CacheThr: reading directory lblock 0
[  622.694838] EXT4-fs warning: 21 callbacks suppressed
[  622.694843] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  622.921837] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  622.921958] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  622.928808] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  622.929829] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  625.853449] EXT4-fs error (device sda1): __ext4_get_inode_loc:3771: inode #14417972: block 57671715: comm BrowserBlocking: unable to read itable block
[  627.356095] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  627.356146] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  629.107310] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #14811503: comm BrowserBlocking: reading directory lblock 0
[  629.107329] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #14811503: comm BrowserBlocking: reading directory lblock 0
[  629.107500] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  633.017087] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  633.017169] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  634.925605] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  634.926073] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  634.927312] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  634.929299] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  634.931900] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  635.517817] EXT4-fs error (device sda1): __ext4_get_inode_loc:3771: inode #14417972: block 57671715: comm BrowserBlocking: unable to read itable block
[  635.925765] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  635.925915] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  638.679823] EXT4-fs warning: 2 callbacks suppressed
[  638.679829] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  638.679977] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  638.680015] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  638.685877] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  638.687584] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  638.688162] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  638.688574] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  638.688618] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  638.689526] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  638.689650] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #14422740: comm Chrome_FileThre: reading directory lblock 0
[  638.689909] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  638.732770] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #14422740: comm BrowserBlocking: reading directory lblock 0
[  641.167153] EXT4-fs error (device sda1): __ext4_get_inode_loc:3771: inode #14417972: block 57671715: comm BrowserBlocking: unable to read itable block
[  643.036502] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #14420095: comm BrowserBlocking: reading directory lblock 0
[  643.932413] EXT4-fs warning: 44 callbacks suppressed
[  643.932420] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  643.932470] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  643.932499] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  644.310967] EXT4-fs warning (device sda1): __ext4_read_dirblock:884: error -5 reading directory block (ino 14681066, block 0)
[  644.730597] EXT4-fs error (device sda1): __ext4_get_inode_loc:3771: inode #14417972: block 57671715: comm BrowserBlocking: unable to read itable block
[  646.119332] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14422747, block 0)
[  646.119350] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14422747, block 0)
[  646.119389] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14422747, block 0)
[  646.119397] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14422747, block 0)
[  646.119838] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  646.937999] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  647.800325] EXT4-fs error (device sda1): __ext4_get_inode_loc:3771: inode #14417972: block 57671715: comm BrowserBlocking: unable to read itable block
[  651.404756] EXT4-fs warning: 7 callbacks suppressed
[  651.404761] EXT4-fs warning (device sda1): __ext4_read_dirblock:884: error -5 reading directory block (ino 14681066, block 0)
[  652.458321] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #14422737: comm Chrome_FileUser: reading directory lblock 0
[  652.458340] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #14422737: comm Chrome_FileUser: reading directory lblock 0
[  652.459758] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  652.720402] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14422747, block 0)
[  652.720418] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14422747, block 0)
[  657.381531] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  658.948394] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  658.948995] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  658.949147] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  658.949354] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  658.949896] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  658.952445] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  658.954220] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  658.954294] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  658.954675] EXT4-fs warning (device sda1): __ext4_read_dirblock:674: error -5 reading directory block (ino 14418409, block 0)
[  658.954730] EXT4-fs warning (device sda1): __ext4_read_dir
```




What can I do? Anyone have ideas? I'd rather not reinstall completely if I don't 100% have to...

---

### Post by dino99 on 2015-06-23
is that /home partition mounted by /etc/fstab ?

---

### Post by Umer_Salman on 2015-06-23
Here is my /etc/fstab

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=9542a4ff-b9d7-4bcc-8c8f-623fd2730bea /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=B6F1-BE40  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=c480afd3-bef0-4020-9a8e-58aeaa889fe3 none            swap    sw              0       0


# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=b249e5d6-3b3e-4cb8-9991-38ac199d589a   /home    ext4          defaults       0  
```

and this is my UUIDs 
[IMG]http://i.imgur.com/b2UWuBt.png[/IMG]

---

### Post by matt_symes on 2015-06-23
Hi

Run a SMART test on the drive and post the results back here.

Is the drive a new drive ? 

Double check the drive is connected correctly and not coming loose.

It looks to be a drive problem of some kind as it is freezing.

Kind regards

---

### Post by Umer_Salman on 2015-06-24
The SMART Extended Test completed without error and is attached. 

[ATTACH]262836[/ATTACH]

Also, the drive is completely new as it was a replacement from HGST of a drive that failed under warranty. 

The drive is connected through the drive bay inside the laptop itself, so there is no room for it to come loose. 

However, the drive hasn't unmounted since yesterday and the only thing I normally run that I haven't is a vagrant virtual machine. I'm going to test this by loading up the virtual machine and see what happens. 

Thanks for the help so far!

---

### Post by tgalati4 on 2015-06-24
It could be a timing issue between the Vagrant virtual machine and the SSD which causes an I/O error and the drive to freeze or go offline.  So if this behavior is consistent, then you might consider filing a bug against your kernel version.  It's also possible that the SATA controller on the laptop is having problems--loose cable or dust on the chipset, that is causing erratic behavior.  What caused your previous drive to fail?  Was the behavior similar?

---

### Post by Umer_Salman on 2015-06-24
I'm not quite sure what you mean by timing error (I don't really know what that is, but I'll Google it in a second) :) 

As for the SATA controller, I don't feel that it's that, but I'll see if I can take a look. 

This laptop used to be my father's, and it had Windows 8 on it. Windows kept blue screening, so I ran SMART tests on it and it failed a part of the SMART test, so I filed an RMA. 
So no, I don't believe the behavior was similar. 

I actually just uninstalled my Vagrant box and reinstalled it, and so far I haven't had an unmount. I think it may have been a bug in Vagrant, but I'll update here if I find out for sure. 

Thanks again!

---

### Post by dino99 on 2015-06-24
modify fstab, it miss the red '2' shown below

UUID=b249e5d6-3b3e-4cb8-9991-38ac199d589a   /home    ext4          defaults       0     [COLOR="#FF0000"] 2[/COLOR]

---

### Post by Umer_Salman on 2015-06-26
Added the 2 in the fstab and had uninstalled/reinstalled Vagrant VMs and it hasn't unmounted in two days. All is well. :) 
Thanks, all!

---

### Post by dino99 on 2015-06-26
> **Umer_Salman said:**
> Added the 2 in the fstab and had uninstalled/reinstalled Vagrant VMs and it hasn't unmounted in two days. All is well. :) 
Thanks, all!

ah, a good news; please set that thread as 'SOLVED' via the 'thread tools' utility found on the top right corner of your first post.

---

