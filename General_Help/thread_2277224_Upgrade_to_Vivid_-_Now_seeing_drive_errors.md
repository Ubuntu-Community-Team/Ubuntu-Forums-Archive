---
title: "Upgrade to Vivid - Now seeing drive errors"
date: 2015-05-07
forum: General Help
---

### Post by jay91 on 2015-05-07
I just upgraded to Vivid and now I'm seeing errors in kern.log. I'm running Ubuntu server diskless and connecting/booting from an iSCSI drive. Never had any problems before. When I do sudo apt-get update I get:
[FONT=arial]Reading package lists... Error!
E: Problem syncing the file - sync (5: Input/output error)
E: The package lists or status file could not be parsed or opened.[/FONT]

None of the suggestions I could find online fix it. Here's my kern.log:

[FONT=arial]May  7 12:09:21 documents kernel: [ 6775.576728] sd 6:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 12:09:21 documents kernel: [ 6775.576753] sd 6:0:0:0: [sda] Sense Key : Illegal Request [current]
May  7 12:09:21 documents kernel: [ 6775.576762] sd 6:0:0:0: [sda] Add. Sense: Invalid field in cdb
May  7 12:09:21 documents kernel: [ 6775.576768] sd 6:0:0:0: [sda] CDB:
May  7 12:09:21 documents kernel: [ 6775.576774] Write(10): 2a 00 00 3e 3f ff 00 40 00 00
May  7 12:09:21 documents kernel: [ 6775.576800] blk_update_request: critical target error, dev sda, sector 4079615
May  7 12:09:21 documents kernel: [ 6775.578444] EXT4-fs warning: 11 callbacks suppressed
May  7 12:09:21 documents kernel: [ 6775.578453] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 221 (offset 0 size 8388608 starting block 510207)
May  7 12:09:21 documents kernel: [ 6775.578461] buffer_io_error: 5121 callbacks suppressed
May  7 12:09:21 documents kernel: [ 6775.578468] Buffer I/O error on device sda1, logical block 501760
May  7 12:09:21 documents kernel: [ 6775.580144] Buffer I/O error on device sda1, logical block 501761
May  7 12:09:21 documents kernel: [ 6775.581801] Buffer I/O error on device sda1, logical block 501762
May  7 12:09:21 documents kernel: [ 6775.583464] Buffer I/O error on device sda1, logical block 501763
May  7 12:09:21 documents kernel: [ 6775.585147] Buffer I/O error on device sda1, logical block 501764
May  7 12:09:21 documents kernel: [ 6775.586812] Buffer I/O error on device sda1, logical block 501765
May  7 12:09:21 documents kernel: [ 6775.588506] Buffer I/O error on device sda1, logical block 501766
May  7 12:09:21 documents kernel: [ 6775.590169] Buffer I/O error on device sda1, logical block 501767
May  7 12:09:21 documents kernel: [ 6775.591834] Buffer I/O error on device sda1, logical block 501768
May  7 12:09:21 documents kernel: [ 6775.593495] Buffer I/O error on device sda1, logical block 501769
May  7 12:09:21 documents kernel: [ 6775.595436] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 221 (offset 0 size 8388608 starting block 510463)
May  7 12:09:21 documents kernel: [ 6775.595811] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 221 (offset 0 size 8388608 starting block 510719)
May  7 12:09:21 documents kernel: [ 6775.596177] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 221 (offset 0 size 8388608 starting block 510975)
May  7 12:09:21 documents kernel: [ 6775.596537] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 221 (offset 0 size 8388608 starting block 511231)
May  7 12:09:21 documents kernel: [ 6775.596904] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 221 (offset 0 size 8388608 starting block 511487)
May  7 12:09:21 documents kernel: [ 6775.597272] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 221 (offset 0 size 8388608 starting block 511743)
May  7 12:09:21 documents kernel: [ 6775.597639] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 221 (offset 0 size 8388608 starting block 511999)
May  7 12:09:21 documents kernel: [ 6775.604836] sd 6:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 12:09:21 documents kernel: [ 6775.604854] sd 6:0:0:0: [sda] Sense Key : Illegal Request [current]
May  7 12:09:21 documents kernel: [ 6775.604863] sd 6:0:0:0: [sda] Add. Sense: Invalid field in cdb
May  7 12:09:21 documents kernel: [ 6775.604872] sd 6:0:0:0: [sda] CDB:
May  7 12:09:21 documents kernel: [ 6775.604877] Write(10): 2a 00 00 3e 7f ff 00 40 00 00
May  7 12:09:21 documents kernel: [ 6775.604893] blk_update_request: critical target error, dev sda, sector 4095999
May  7 12:09:21 documents kernel: [ 6775.606595] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 221 (offset 8388608 size 8388608 starting block 512255)
May  7 12:09:21 documents kernel: [ 6775.606977] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 221 (offset 8388608 size 8388608 starting block 512511)
May  7 12:09:21 documents kernel: [ 6775.616787] sd 6:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 12:09:21 documents kernel: [ 6775.616797] sd 6:0:0:0: [sda] Sense Key : Illegal Request [current]
May  7 12:09:21 documents kernel: [ 6775.616802] sd 6:0:0:0: [sda] Add. Sense: Invalid field in cdb
May  7 12:09:21 documents kernel: [ 6775.616805] sd 6:0:0:0: [sda] CDB:
May  7 12:09:21 documents kernel: [ 6775.616809] Write(10): 2a 00 00 3e bf ff 00 40 00 00
May  7 12:09:21 documents kernel: [ 6775.616821] blk_update_request: critical target error, dev sda, sector 4112383
May  7 12:09:21 documents kernel: [ 6775.627182] sd 6:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 12:09:21 documents kernel: [ 6775.627186] sd 6:0:0:0: [sda] Sense Key : Illegal Request [current]
May  7 12:09:21 documents kernel: [ 6775.627189] sd 6:0:0:0: [sda] Add. Sense: Invalid field in cdb
May  7 12:09:21 documents kernel: [ 6775.627191] sd 6:0:0:0: [sda] CDB:
May  7 12:09:21 documents kernel: [ 6775.627192] Write(10): 2a 00 00 3e ff ff 00 40 00 00
May  7 12:09:21 documents kernel: [ 6775.627201] blk_update_request: critical target error, dev sda, sector 4128767
May  7 12:09:21 documents kernel: [ 6775.637989] sd 6:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 12:09:21 documents kernel: [ 6775.637998] sd 6:0:0:0: [sda] Sense Key : Illegal Request [current]
May  7 12:09:21 documents kernel: [ 6775.638002] sd 6:0:0:0: [sda] Add. Sense: Invalid field in cdb
May  7 12:09:21 documents kernel: [ 6775.638006] sd 6:0:0:0: [sda] CDB:
May  7 12:09:21 documents kernel: [ 6775.638009] Write(10): 2a 00 00 3f bf ff 00 3a 58 00
May  7 12:09:21 documents kernel: [ 6775.638022] blk_update_request: critical target error, dev sda, sector 4177919
May  7 12:09:47 documents kernel: [ 6801.840365] sd 6:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 12:09:47 documents kernel: [ 6801.840386] sd 6:0:0:0: [sda] Sense Key : Illegal Request [current]
May  7 12:09:47 documents kernel: [ 6801.840395] sd 6:0:0:0: [sda] Add. Sense: Invalid field in cdb
May  7 12:09:47 documents kernel: [ 6801.840403] sd 6:0:0:0: [sda] CDB:
May  7 12:09:47 documents kernel: [ 6801.840408] Write(10): 2a 00 00 1d 7f ff 00 27 08 00
May  7 12:09:47 documents kernel: [ 6801.840426] blk_update_request: critical target error, dev sda, sector 1933311
May  7 12:09:47 documents kernel: [ 6801.842143] EXT4-fs warning: 30 callbacks suppressed
May  7 12:09:47 documents kernel: [ 6801.842153] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 448 (offset 0 size 5115904 starting block 241919)
May  7 12:09:47 documents kernel: [ 6801.842161] buffer_io_error: 10049 callbacks suppressed
May  7 12:09:47 documents kernel: [ 6801.842166] Buffer I/O error on device sda1, logical block 233472
May  7 12:09:47 documents kernel: [ 6801.843846] Buffer I/O error on device sda1, logical block 233473
May  7 12:09:47 documents kernel: [ 6801.845487] Buffer I/O error on device sda1, logical block 233474
May  7 12:09:47 documents kernel: [ 6801.847144] Buffer I/O error on device sda1, logical block 233475
May  7 12:09:47 documents kernel: [ 6801.848799] Buffer I/O error on device sda1, logical block 233476
May  7 12:09:47 documents kernel: [ 6801.850449] Buffer I/O error on device sda1, logical block 233477
May  7 12:09:47 documents kernel: [ 6801.852121] Buffer I/O error on device sda1, logical block 233478
May  7 12:09:47 documents kernel: [ 6801.853772] Buffer I/O error on device sda1, logical block 233479
May  7 12:09:47 documents kernel: [ 6801.855433] Buffer I/O error on device sda1, logical block 233480
May  7 12:09:47 documents kernel: [ 6801.857080] Buffer I/O error on device sda1, logical block 233481
May  7 12:09:47 documents kernel: [ 6801.858919] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 448 (offset 0 size 5115904 starting block 242175)
May  7 12:09:47 documents kernel: [ 6801.859139] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 448 (offset 0 size 5115904 starting block 242431)
May  7 12:09:47 documents kernel: [ 6801.859341] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 448 (offset 0 size 5115904 starting block 242687)
May  7 12:09:47 documents kernel: [ 6801.859545] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 448 (offset 0 size 5115904 starting block 242912)
May  7 12:09:47 documents kernel: [ 6801.867102] sd 6:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 12:09:47 documents kernel: [ 6801.867109] sd 6:0:0:0: [sda] Sense Key : Illegal Request [current]
May  7 12:09:47 documents kernel: [ 6801.867114] sd 6:0:0:0: [sda] Add. Sense: Invalid field in cdb
May  7 12:09:47 documents kernel: [ 6801.867117] sd 6:0:0:0: [sda] CDB:
May  7 12:09:47 documents kernel: [ 6801.867120] Write(10): 2a 00 00 3f ff ff 00 40 00 00
May  7 12:09:47 documents kernel: [ 6801.867135] blk_update_request: critical target error, dev sda, sector 4194303
May  7 12:09:47 documents kernel: [ 6801.868836] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 908 (offset 0 size 8388608 starting block 524543)
May  7 12:09:47 documents kernel: [ 6801.869039] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 908 (offset 0 size 8388608 starting block 524799)
May  7 12:09:47 documents kernel: [ 6801.869234] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 908 (offset 0 size 8388608 starting block 525055)
May  7 12:09:47 documents kernel: [ 6801.869429] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 908 (offset 0 size 8388608 starting block 525311)
May  7 12:09:47 documents kernel: [ 6801.869624] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 908 (offset 0 size 8388608 starting block 525567)
May  7 12:09:47 documents kernel: [ 6801.873826] sd 6:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 12:09:47 documents kernel: [ 6801.873837] sd 6:0:0:0: [sda] Sense Key : Illegal Request [current]
May  7 12:09:47 documents kernel: [ 6801.873841] sd 6:0:0:0: [sda] Add. Sense: Invalid field in cdb
May  7 12:09:47 documents kernel: [ 6801.873845] sd 6:0:0:0: [sda] CDB:
May  7 12:09:47 documents kernel: [ 6801.873848] Write(10): 2a 00 00 4d 7f ff 00 40 00 00
May  7 12:09:47 documents kernel: [ 6801.873860] blk_update_request: critical target error, dev sda, sector 5079039
May  7 12:09:47 documents kernel: [ 6801.880327] sd 6:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 12:09:47 documents kernel: [ 6801.880331] sd 6:0:0:0: [sda] Sense Key : Illegal Request [current]
May  7 12:09:47 documents kernel: [ 6801.880334] sd 6:0:0:0: [sda] Add. Sense: Invalid field in cdb
May  7 12:09:47 documents kernel: [ 6801.880336] sd 6:0:0:0: [sda] CDB:
May  7 12:09:47 documents kernel: [ 6801.880337] Write(10): 2a 00 00 4e 3f ff 00 40 00 00
May  7 12:09:48 documents kernel: [ 6802.001733] blk_update_request: critical target error, dev sda, sector 5275647
May  7 12:09:52 documents kernel: [ 6806.950296] sd 6:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 12:09:52 documents kernel: [ 6806.950300] sd 6:0:0:0: [sda] Sense Key : Illegal Request [current]
May  7 12:09:52 documents kernel: [ 6806.950303] sd 6:0:0:0: [sda] Add. Sense: Invalid field in cdb
May  7 12:09:52 documents kernel: [ 6806.950304] sd 6:0:0:0: [sda] CDB:
May  7 12:09:52 documents kernel: [ 6806.950306] Write(10): 2a 00 00 56 92 2f 00 3f 50 00
May  7 12:09:52 documents kernel: [ 6806.950312] blk_update_request: critical target error, dev sda, sector 5673519
May  7 12:09:52 documents kernel: [ 6806.951751] EXT4-fs warning: 65 callbacks suppressed
May  7 12:09:52 documents kernel: [ 6806.951754] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 1453 (offset 0 size 8298496 starting block 709445)
May  7 12:09:52 documents kernel: [ 6806.951756] buffer_io_error: 19041 callbacks suppressed
May  7 12:09:52 documents kernel: [ 6806.951757] Buffer I/O error on device sda1, logical block 700998
May  7 12:09:52 documents kernel: [ 6806.953222] Buffer I/O error on device sda1, logical block 700999
May  7 12:09:52 documents kernel: [ 6806.954661] Buffer I/O error on device sda1, logical block 701000
May  7 12:09:52 documents kernel: [ 6806.956114] Buffer I/O error on device sda1, logical block 701001
May  7 12:09:52 documents kernel: [ 6806.957543] Buffer I/O error on device sda1, logical block 701002
May  7 12:09:52 documents kernel: [ 6806.958988] Buffer I/O error on device sda1, logical block 701003
May  7 12:09:52 documents kernel: [ 6806.960377] Buffer I/O error on device sda1, logical block 701004
May  7 12:09:52 documents kernel: [ 6806.961737] Buffer I/O error on device sda1, logical block 701005
May  7 12:09:52 documents kernel: [ 6806.963134] Buffer I/O error on device sda1, logical block 701006
May  7 12:09:52 documents kernel: [ 6806.964500] Buffer I/O error on device sda1, logical block 701007
May  7 12:09:52 documents kernel: [ 6806.965911] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 1453 (offset 0 size 8298496 starting block 709701)
May  7 12:09:52 documents kernel: [ 6806.965982] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 1453 (offset 0 size 8298496 starting block 709957)
May  7 12:09:52 documents kernel: [ 6806.966053] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 1453 (offset 0 size 8298496 starting block 710213)
May  7 12:09:52 documents kernel: [ 6806.966125] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 1453 (offset 0 size 8298496 starting block 710469)
May  7 12:09:52 documents kernel: [ 6806.966196] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 1453 (offset 0 size 8298496 starting block 710725)
May  7 12:09:52 documents kernel: [ 6806.966266] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 1453 (offset 0 size 8298496 starting block 710981)
May  7 12:09:52 documents kernel: [ 6806.966337] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 1453 (offset 0 size 8298496 starting block 711215)
May  7 12:09:53 documents kernel: [ 6807.021672] sd 6:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 12:09:53 documents kernel: [ 6807.021679] sd 6:0:0:0: [sda] Sense Key : Illegal Request [current]
May  7 12:09:53 documents kernel: [ 6807.021684] sd 6:0:0:0: [sda] Add. Sense: Invalid field in cdb
May  7 12:09:53 documents kernel: [ 6807.021688] sd 6:0:0:0: [sda] CDB:
May  7 12:09:53 documents kernel: [ 6807.021691] Write(10): 2a 00 00 50 bf ff 00 40 00 00
May  7 12:09:53 documents kernel: [ 6807.021707] blk_update_request: critical target error, dev sda, sector 5292031
May  7 12:09:53 documents kernel: [ 6807.023422] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 1684 (offset 0 size 8388608 starting block 661759)
May  7 12:09:53 documents kernel: [ 6807.023649] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -121 writing to inode 1684 (offset 0 size 8388608 starting block 662015)
May  7 12:09:53 documents kernel: [ 6807.028153] sd 6:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 12:09:53 documents kernel: [ 6807.028170] sd 6:0:0:0: [sda] Sense Key : Illegal Request [current]
May  7 12:09:53 documents kernel: [ 6807.028177] sd 6:0:0:0: [sda] Add. Sense: Invalid field in cdb
May  7 12:09:53 documents kernel: [ 6807.028184] sd 6:0:0:0: [sda] CDB:
May  7 12:09:53 documents kernel: [ 6807.028192] Write(10): 2a 00 00 50 ff ff 00 40 00 00
May  7 12:09:53 documents kernel: [ 6807.028209] blk_update_request: critical target error, dev sda, sector 5308415
May  7 12:09:53 documents kernel: [ 6807.034566] sd 6:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 12:09:53 documents kernel: [ 6807.034583] sd 6:0:0:0: [sda] Sense Key : Illegal Request [current]
May  7 12:09:53 documents kernel: [ 6807.034590] sd 6:0:0:0: [sda] Add. Sense: Invalid field in cdb
May  7 12:09:53 documents kernel: [ 6807.034596] sd 6:0:0:0: [sda] CDB:
May  7 12:09:53 documents kernel: [ 6807.034602] Write(10): 2a 00 00 51 3f ff 00 40 00 00
May  7 12:09:53 documents kernel: [ 6807.266401] sd 6:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  7 12:09:53 documents kernel: [ 6807.266418] sd 6:0:0:0: [sda] Sense Key : Illegal Request [current]
May  7 12:09:53 documents kernel: [ 6807.266426] sd 6:0:0:0: [sda] Add. Sense: Invalid field in cdb
May  7 12:09:53 documents kernel: [ 6807.266432] sd 6:0:0:0: [sda] CDB:
May  7 12:09:53 documents kernel: [ 6807.266440] Write(10): 2a 00 00 55 7f ff 00 40 00 00
May  7 12:09:53 documents kernel: [ 6807.266457] blk_update_request: critical target error, dev sda, sector 5603327[/FONT]

I booted to a live CD and did fsck to fix it but when I boot up again, after I run apt-get it starts erroring out on me.
Any help would be greatly appreciated.

---

