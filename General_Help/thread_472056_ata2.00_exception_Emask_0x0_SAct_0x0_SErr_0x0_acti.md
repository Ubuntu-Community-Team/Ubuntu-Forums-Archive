---
title: "ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action"
date: 2007-06-12
forum: General Help
---

### Post by mr_static on 2007-06-12
Hey i'm getting some disk error's hope some one can help me

Using ubuntu 7.04 server edition, i have looked a little into it and thought it was something todo with piix?



> un 13 00:08:33 AMBERT kernel: [  233.112658] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jun 13 00:08:33 AMBERT kernel: [  233.112734] ata2.00: cmd c8/00:08:cf:81:85/00:00:00:00:00/e4 tag 0 cdb 0x0 data 4096 in
Jun 13 00:08:33 AMBERT kernel: [  233.112736]          res 51/40:00:cf:81:85/00:00:00:00:00/e4 Emask 0x9 (media error)
Jun 13 00:08:33 AMBERT kernel: [  233.140616] ata2.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728
Jun 13 00:08:33 AMBERT kernel: [  233.160575] ata2.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728
Jun 13 00:08:33 AMBERT kernel: [  233.160579] ata2.00: configured for UDMA/133
Jun 13 00:08:33 AMBERT kernel: [  233.160588] ata2: EH complete
Jun 13 00:08:35 AMBERT kernel: [  234.253310] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jun 13 00:08:35 AMBERT kernel: [  234.253383] ata2.00: cmd c8/00:08:cf:81:85/00:00:00:00:00/e4 tag 0 cdb 0x0 data 4096 in
Jun 13 00:08:35 AMBERT kernel: [  234.253385]          res 51/40:00:cf:81:85/00:00:00:00:00/e4 Emask 0x9 (media error)
Jun 13 00:08:35 AMBERT kernel: [  234.279411] ata2.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728
Jun 13 00:08:35 AMBERT kernel: [  234.299393] ata2.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728
Jun 13 00:08:35 AMBERT kernel: [  234.299398] ata2.00: configured for UDMA/133
Jun 13 00:08:35 AMBERT kernel: [  234.299409] ata2: EH complete
Jun 13 00:08:36 AMBERT kernel: [  235.527152] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jun 13 00:08:36 AMBERT kernel: [  235.527219] ata2.00: cmd c8/00:08:cf:81:85/00:00:00:00:00/e4 tag 0 cdb 0x0 data 4096 in
Jun 13 00:08:36 AMBERT kernel: [  235.527221]          res 51/40:00:cf:81:85/00:00:00:00:00/e4 Emask 0x9 (media error)
Jun 13 00:08:36 AMBERT kernel: [  235.548071] ata2.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728
Jun 13 00:08:36 AMBERT kernel: [  235.568049] ata2.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728
Jun 13 00:08:36 AMBERT kernel: [  235.568053] ata2.00: configured for UDMA/133
Jun 13 00:08:36 AMBERT kernel: [  235.568058] ata2: EH complete
Jun 13 00:08:38 AMBERT kernel: [  238.091533] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jun 13 00:08:38 AMBERT kernel: [  238.091601] ata2.00: cmd c8/00:08:cf:81:85/00:00:00:00:00/e4 tag 0 cdb 0x0 data 4096 in
Jun 13 00:08:38 AMBERT kernel: [  238.091603]          res 51/01:00:cf:81:85/00:00:00:00:00/e4 Emask 0x1 (device error)
Jun 13 00:08:38 AMBERT kernel: [  238.115383] ata2.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728
Jun 13 00:08:38 AMBERT kernel: [  238.135373] ata2.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728
Jun 13 00:08:38 AMBERT kernel: [  238.135377] ata2.00: configured for UDMA/133
Jun 13 00:08:38 AMBERT kernel: [  238.135384] ata2: EH complete
Jun 13 00:08:40 AMBERT kernel: [  239.365387] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jun 13 00:08:40 AMBERT kernel: [  239.365455] ata2.00: cmd c8/00:08:cf:81:85/00:00:00:00:00/e4 tag 0 cdb 0x0 data 4096 in
Jun 13 00:08:40 AMBERT kernel: [  239.365456]          res 51/40:00:cf:81:85/00:00:00:00:00/e4 Emask 0x9 (media error)
Jun 13 00:08:40 AMBERT kernel: [  239.394057] ata2.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728
Jun 13 00:08:40 AMBERT kernel: [  239.414014] ata2.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728
Jun 13 00:08:40 AMBERT kernel: [  239.414018] ata2.00: configured for UDMA/133
Jun 13 00:08:40 AMBERT kernel: [  239.414024] ata2: EH complete
Jun 13 00:08:41 AMBERT kernel: [  240.514361] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jun 13 00:08:41 AMBERT kernel: [  240.514428] ata2.00: cmd c8/00:08:cf:81:85/00:00:00:00:00/e4 tag 0 cdb 0x0 data 4096 in
Jun 13 00:08:41 AMBERT kernel: [  240.514430]          res 51/40:00:cf:81:85/00:00:00:00:00/e4 Emask 0x9 (media error)
Jun 13 00:08:41 AMBERT kernel: [  240.542834] ata2.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728
Jun 13 00:08:41 AMBERT kernel: [  240.562812] ata2.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728
Jun 13 00:08:41 AMBERT kernel: [  240.562816] ata2.00: configured for UDMA/133
Jun 13 00:08:41 AMBERT kernel: [  240.562828] sd 1:0:0:0: SCSI error: return code = 0x08000002
Jun 13 00:08:41 AMBERT kernel: [  240.562832] sdb: Current [descriptor]: sense key: Medium Error
Jun 13 00:08:41 AMBERT kernel: [  240.562835]     Additional sense: Unrecovered read error - auto reallocate failed
Jun 13 00:08:41 AMBERT kernel: [  240.562841] Descriptor sense data with sense descriptors (in hex):
Jun 13 00:08:41 AMBERT kernel: [  240.562843]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jun 13 00:08:41 AMBERT kernel: [  240.562850]         04 85 81 cf 
Jun 13 00:08:41 AMBERT kernel: [  240.562853] end_request: I/O error, dev sdb, sector 75858383
Jun 13 00:08:41 AMBERT kernel: [  240.562865] ata2: EH complete
Jun 13 00:08:41 AMBERT kernel: [  240.563577] EXT3-fs error (device dm-0): ext3_get_inode_loc: unable to read inode block - inode=54525953, block=109051906
Jun 13 00:08:41 AMBERT kernel: [  240.564595] SCSI device sdb: 240121728 512-byte hdwr sectors (122942 MB)
Jun 13 00:08:41 AMBERT kernel: [  240.567420] sdb: Write Protect is off
Jun 13 00:08:41 AMBERT kernel: [  240.567424] sdb: Mode Sense: 00 3a 00 00
Jun 13 00:08:41 AMBERT kernel: [  240.570725] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 13 00:08:41 AMBERT kernel: [  240.571207] SCSI device sdb: 240121728 512-byte hdwr sectors (122942 MB)
Jun 13 00:08:41 AMBERT kernel: [  240.571262] sdb: Write Protect is off
Jun 13 00:08:41 AMBERT kernel: [  240.571265] sdb: Mode Sense: 00 3a 00 00
Jun 13 00:08:41 AMBERT kernel: [  240.571889] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 13 00:09:13 AMBERT kernel: [  272.958285] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

---

### Post by werrior on 2007-07-12
I am getting the same error.  Did you have any luck with it?  I am assuming that my HD is bad.

---

### Post by ubuntu_demon on 2007-10-12
to mr_static and werrior :

What version of Ubuntu are you running ?
Did you figure our whether your harddrive is dying or whether it is some other problem ?

I'm dual-booting Feisty and Gutsy and I might be experiencing a similar problem :
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/151938](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/151938)
[http://ubuntudemon.wordpress.com/2007/10/12/bug-151938-in-linux-source-2622/](http://ubuntudemon.wordpress.com/2007/10/12/bug-151938-in-linux-source-2622/)

thanks for the information :)

---

### Post by viper233 on 2007-11-04
Similar errors, don't know if the drive is bad, smartctl says it's fine

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/151938](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/151938)

---

### Post by ubuntu_demon on 2007-11-07
> **viper233 said:**
> Similar errors, don't know if the drive is bad, smartctl says it's fine

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/151938](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/151938)

I reported that bug. It turned out it was an invalid bug since it was my harddrive that was dying.

If you have similar errors you should backup all your data and use the diagnostic tool recommended by your harddrive manufacturer. It might be included on the Ultimate Boot cd-rom. You might need to buy a new harddrive.

I'm interested in whether your Load_Cycle_Count has anything to do with your harddrive problems.

$sudo aptitude install smartmontools
$sudo smartctl -a /dev/sda | grep Load_Cycle_Count

see also :
[http://ubuntuforums.org/showpost.php?p=3675784&postcount=25](http://ubuntuforums.org/showpost.php?p=3675784&postcount=25)
[http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

---

### Post by ubuntu_demon on 2007-11-21
viper233 did you get a new drive ? How old was your drive ? Can you give me the Load_Cycle_Count line of your defected drive ?

---

### Post by slayer^_^ on 2008-03-09
to me the solution was unplugging the SATA data and power cables, substituting the data ones and switching the power ones... maybe a simple contact mechanical error, due to the fact that this kinda cable are more fragile than the old ide ones...

---

### Post by KeyserSoze93 on 2008-03-09
For me, it was the power supply... my system would freeze, lock etc. and need to be rebooted. Log showed similar error messages. Now I have a new PSU and it works like a dream...

---

### Post by harjinder1988 on 2008-05-13
I have got the same problem


Had two installations of Ubuntu 7.04 
upgraded one to 8.04 using distribution upgrade and now cant get ne of dem working 
getting same message

ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata2.00: (BMDMA stat 0x25)
ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0


on booting the hard drive
0+ processors (version 2.00.00)
[ 627.807833] powernow-k8: MP systems not supported by PSB BIOS structure
[ 627.808030] powernow-k8: MP systems not supported by PSB BIOS structure
[ 632.805760] lp0: using parport0 (interrupt-driven).
[ 633.958279] ppdev: user-space parallel port driver
[ 635.268101] eth0: no link during initialization.
[ 638.389465] Failure registering capabilities with primary security module.
[ 639.292524] Bluetooth: Core ver 2.11
[ 639.292683] NET: Registered protocol family 31
[ 639.292686] Bluetooth: HCI device and connection manager initialized
[ 639.292690] Bluetooth: HCI socket layer initialized
[ 639.376389] Bluetooth: L2CAP ver 2.8
[ 639.376393] Bluetooth: L2CAP socket layer initialized
[ 639.921649] Bluetooth: RFCOMM socket layer initialized
[ 639.921669] Bluetooth: RFCOMM TTY layer initialized
[ 639.921671] Bluetooth: RFCOMM ver 1.8
[ 788.594559] end_request: I/O error, dev fd0, sector 0
[ 800.775717] end_request: I/O error, dev fd0, sector 0
[ 812.957550] end_request: I/O error, dev fd0, sector 0
[ 825.132448] end_request: I/O error, dev fd0, sector 0
[ 837.306252] end_request: I/O error, dev fd0, sector 0
[ 837.306258] Buffer I/O error on device fd0, logical block 0
[ 849.479961] end_request: I/O error, dev fd0, sector 0
[ 849.479968] Buffer I/O error on device fd0, logical block 0
[ 861.641668] end_request: I/O error, dev fd0, sector 0
[ 861.641674] Buffer I/O error on device fd0, logical block 0
[ 873.887443] end_request: I/O error, dev fd0, sector 0
[ 873.887449] Buffer I/O error on device fd0, logical block 0
[ 886.133416] end_request: I/O error, dev fd0, sector 0
[ 886.133423] Buffer I/O error on device fd0, logical block 0
[ 898.367440] end_request: I/O error, dev fd0, sector 0
[ 898.367445] Buffer I/O error on device fd0, logical block 0
[ 910.590083] end_request: I/O error, dev fd0, sector 0
[ 910.590090] Buffer I/O error on device fd0, logical block 0
[ 922.811951] end_request: I/O error, dev fd0, sector 0
[ 922.811957] Buffer I/O error on device fd0, logical block 0
[ 935.025584] end_request: I/O error, dev fd0, sector 0
[ 935.025590] Buffer I/O error on device fd0, logical block 0
[ 947.231221] end_request: I/O error, dev fd0, sector 0
[ 947.231227] Buffer I/O error on device fd0, logical block 0
[ 959.429869] end_request: I/O error, dev fd0, sector 0
[ 959.429875] Buffer I/O error on device fd0, logical block 0
[ 971.611047] end_request: I/O error, dev fd0, sector 0
[ 971.611054] Buffer I/O error on device fd0, logical block 0
[ 983.797448] end_request: I/O error, dev fd0, sector 0
[ 983.797454] Buffer I/O error on device fd0, logical block 0
[ 995.983449] end_request: I/O error, dev fd0, sector 0
[ 995.983455] Buffer I/O error on device fd0, logical block 0
[ 1008.173065] end_request: I/O error, dev fd0, sector 0
[ 1008.173071] Buffer I/O error on device fd0, logical block 0
[ 1020.363258] end_request: I/O error, dev fd0, sector 0
[ 1020.363265] Buffer I/O error on device fd0, logical block 0
[ 1032.548839] end_request: I/O error, dev fd0, sector 0
[ 1044.731635] end_request: I/O error, dev fd0, sector 0
[ 1056.917578] end_request: I/O error, dev fd0, sector 0
[ 1069.098891] end_request: I/O error, dev fd0, sector 0
[ 1069.098897] Buffer I/O error on device fd0, logical block 0
[ 1081.272733] end_request: I/O error, dev fd0, sector 0
[ 1081.272740] Buffer I/O error on device fd0, logical block 0
[ 1088.524061] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1088.524067] ata2.00: (BMDMA stat 0x25)
[ 1088.524072] ata2.00: cmd c8/00:2c:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 22528 in
[ 1088.524073] res 51/40:09:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1088.547365] ata2.00: configured for UDMA/133
[ 1088.547373] ata2: EH complete
[ 1093.189533] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1093.189537] ata2.00: (BMDMA stat 0x25)
[ 1093.189541] ata2.00: cmd c8/00:2c:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 22528 in
[ 1093.189543] res 51/40:09:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1093.214582] ata2.00: configured for UDMA/133
[ 1093.214589] ata2: EH complete
[ 1097.871671] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1097.871676] ata2.00: (BMDMA stat 0x25)
[ 1097.871681] ata2.00: cmd c8/00:2c:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 22528 in
[ 1097.871682] res 51/40:09:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1097.893798] ata2.00: configured for UDMA/133
[ 1097.893806] ata2: EH complete
[ 1102.578803] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1102.578808] ata2.00: (BMDMA stat 0x25)
[ 1102.578812] ata2.00: cmd c8/00:2c:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 22528 in
[ 1102.578813] res 51/40:09:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1102.601008] ata2.00: configured for UDMA/133
[ 1102.601015] ata2: EH complete
[ 1107.319261] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1107.319265] ata2.00: (BMDMA stat 0x25)
[ 1107.319269] ata2.00: cmd c8/00:2c:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 22528 in
[ 1107.319270] res 51/40:09:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1107.340216] ata2.00: configured for UDMA/133
[ 1107.340223] ata2: EH complete
[ 1112.051388] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1112.051392] ata2.00: (BMDMA stat 0x25)
[ 1112.051397] ata2.00: cmd c8/00:2c:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 22528 in
[ 1112.051398] res 51/40:09:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1112.075422] ata2.00: configured for UDMA/133
[ 1112.075449] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1112.075452] sd 1:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1112.075455] Descriptor sense data with sense descriptors (in hex):
[ 1112.075457] 72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[ 1112.075462] 00 00 00 84
[ 1112.075464] sd 1:0:0:0: [sda] Add. Sense: Unrecovered read error -
auto reallocate failed
[ 1112.075468] end_request: I/O error, dev sda, sector 132
[ 1112.075471] Buffer I/O error on device sda1, logical block 34
[ 1112.075474] Buffer I/O error on device sda1, logical block 35
[ 1112.075477] Buffer I/O error on device sda1, logical block 36
[ 1112.075479] Buffer I/O error on device sda1, logical block 37
[ 1112.075481] Buffer I/O error on device sda1, logical block 38
[ 1112.075490] ata2: EH complete
[ 1112.102066] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 1116.758524] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1116.758529] ata2.00: (BMDMA stat 0x25)
[ 1116.758534] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1116.758535] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1116.782633] ata2.00: configured for UDMA/133
[ 1116.782642] ata2: EH complete
[ 1121.440661] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1121.440666] ata2.00: (BMDMA stat 0x25)
[ 1121.440670] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1121.440671] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1121.461849] ata2.00: configured for UDMA/133
[ 1121.461857] ata2: EH complete
[ 1126.172786] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1126.172790] ata2.00: (BMDMA stat 0x25)
[ 1126.172795] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1126.172796] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1126.197056] ata2.00: configured for UDMA/133
[ 1126.197063] ata2: EH complete
[ 1130.921573] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1130.921576] ata2.00: (BMDMA stat 0x25)
[ 1130.921581] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1130.921582] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1130.944260] ata2.00: configured for UDMA/133
[ 1130.944266] ata2: EH complete
[ 1135.670363] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1135.670367] ata2.00: (BMDMA stat 0x25)
[ 1135.670371] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1135.670372] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1135.691466] ata2.00: configured for UDMA/133
[ 1135.691472] ata2: EH complete
[ 1140.360841] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1140.360846] ata2.00: (BMDMA stat 0x25)
[ 1140.360851] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1140.360852] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1140.382678] ata2.00: configured for UDMA/133
[ 1140.382692] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1140.382695] sd 1:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1140.382698] Descriptor sense data with sense descriptors (in hex):
[ 1140.382700] 72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[ 1140.382704] 00 00 00 84
[ 1140.382707] sd 1:0:0:0: [sda] Add. Sense: Unrecovered read error -
auto reallocate failed
[ 1140.382711] end_request: I/O error, dev sda, sector 132
[ 1140.382714] Buffer I/O error on device sda1, logical block 34
[ 1140.382718] Buffer I/O error on device sda1, logical block 35
[ 1140.382731] ata2: EH complete
[ 1140.385398] sd 1:0:0:0: [sda] Write Protect is off
[ 1140.385401] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1140.386455] sd 1:0:0:0: [sda] Write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[ 1140.388260] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 1140.388340] sd 1:0:0:0: [sda] Write Protect is off
[ 1140.388343] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1140.388755] sd 1:0:0:0: [sda] Write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[ 1145.134623] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1145.134628] ata2.00: (BMDMA stat 0x25)
[ 1145.134633] ata2.00: cmd c8/00:3e:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 31744 in
[ 1145.134635] res 51/40:1b:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1145.169878] ata2.00: configured for UDMA/133
[ 1145.169886] ata2: EH complete
[ 1149.833420] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1149.833424] ata2.00: (BMDMA stat 0x25)
[ 1149.833429] ata2.00: cmd c8/00:3e:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 31744 in
[ 1149.833430] res 51/40:1b:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1149.869088] ata2.00: configured for UDMA/133
[ 1149.869097] ata2: EH complete
[ 1154.523890] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1154.523894] ata2.00: (BMDMA stat 0x25)
[ 1154.523898] ata2.00: cmd c8/00:3e:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 31744 in
[ 1154.523899] res 51/40:1b:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1154.552302] ata2.00: configured for UDMA/133
[ 1154.552308] ata2: EH complete
[ 1159.239353] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1159.239357] ata2.00: (BMDMA stat 0x25)
[ 1159.239362] ata2.00: cmd c8/00:3e:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 31744 in
[ 1159.239363] res 51/40:1b:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1159.267513] ata2.00: configured for UDMA/133
[ 1159.267520] ata2: EH complete
[ 1163.921493] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1163.921496] ata2.00: (BMDMA stat 0x25)
[ 1163.921501] ata2.00: cmd c8/00:3e:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 31744 in
[ 1163.921502] res 51/40:1b:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1163.950730] ata2.00: configured for UDMA/133
[ 1163.950737] ata2: EH complete
[ 1168.636957] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1168.636961] ata2.00: (BMDMA stat 0x25)
[ 1168.636966] ata2.00: cmd c8/00:3e:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 31744 in
[ 1168.636967] res 51/40:1b:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1168.661940] ata2.00: configured for UDMA/133
[ 1168.661968] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1168.661971] sd 1:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1168.661975] Descriptor sense data with sense descriptors (in hex):
[ 1168.661976] 72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[ 1168.661981] 00 00 00 84
[ 1168.661983] sd 1:0:0:0: [sda] Add. Sense: Unrecovered read error -
auto reallocate failed
[ 1168.661987] end_request: I/O error, dev sda, sector 132
[ 1168.661990] Buffer I/O error on device sda1, logical block 34
[ 1168.661993] Buffer I/O error on device sda1, logical block 35
[ 1168.661996] Buffer I/O error on device sda1, logical block 36
[ 1168.661999] Buffer I/O error on device sda1, logical block 37
[ 1168.662001] Buffer I/O error on device sda1, logical block 38
[ 1168.662004] Buffer I/O error on device sda1, logical block 39
[ 1168.662006] Buffer I/O error on device sda1, logical block 40
[ 1168.662009] Buffer I/O error on device sda1, logical block 41
[ 1168.662011] Buffer I/O error on device sda1, logical block 42
[ 1168.662013] Buffer I/O error on device sda1, logical block 43
[ 1168.662024] ata2: EH complete
[ 1168.687636] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 1173.352424] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1173.352429] ata2.00: (BMDMA stat 0x25)
[ 1173.352433] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1173.352435] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1173.377150] ata2.00: configured for UDMA/133
[ 1173.377158] ata2: EH complete
[ 1178.042893] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1178.042897] ata2.00: (BMDMA stat 0x25)
[ 1178.042901] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1178.042903] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1178.068363] ata2.00: configured for UDMA/133
[ 1178.068370] ata2: EH complete
[ 1182.691705] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1182.691709] ata2.00: (BMDMA stat 0x25)
[ 1182.691713] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1182.691714] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1182.715584] ata2.00: configured for UDMA/133
[ 1182.715591] ata2: EH complete
[ 1187.348852] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1187.348856] ata2.00: (BMDMA stat 0x25)
[ 1187.348860] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1187.348861] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1187.374803] ata2.00: configured for UDMA/133
[ 1187.374810] ata2: EH complete
[ 1192.022660] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1192.022664] ata2.00: (BMDMA stat 0x25)
[ 1192.022668] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1192.022669] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1192.050021] ata2.00: configured for UDMA/133
[ 1192.050029] ata2: EH complete
[ 1196.788111] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1196.788115] ata2.00: (BMDMA stat 0x25)
[ 1196.788119] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1196.788120] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1196.813223] ata2.00: configured for UDMA/133
[ 1196.813233] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1196.813236] sd 1:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1196.813239] Descriptor sense data with sense descriptors (in hex):
[ 1196.813241] 72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[ 1196.813246] 00 00 00 84
[ 1196.813248] sd 1:0:0:0: [sda] Add. Sense: Unrecovered read error -
auto reallocate failed
[ 1196.813252] end_request: I/O error, dev sda, sector 132
[ 1196.813254] printk: 4 messages suppressed.
[ 1196.813256] Buffer I/O error on device sda1, logical block 34
[ 1196.813260] Buffer I/O error on device sda1, logical block 35
[ 1196.813270] ata2: EH complete
[ 1196.813441] sd 1:0:0:0: [sda] Write Protect is off
[ 1196.813443] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1196.815597] sd 1:0:0:0: [sda] Write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[ 1196.815671] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 1196.815700] sd 1:0:0:0: [sda] Write Protect is off
[ 1196.815702] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1196.817274] sd 1:0:0:0: [sda] Write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[ 1262.059457] NET: Registered protocol family 10
[ 1262.059720] lo: Disabled Privacy Extensions
[ 1262.060028] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1347.099108] eth0: link up.
[ 1347.099925] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1349.527667] NET: Registered protocol family 17
[ 1352.476281] eth0: link down.
[ 1354.127828] eth0: link up.
[ 1354.128647] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1354.898346] usb 1-5: new full speed USB device using ohci_hcd and address 2
[ 1355.119580] usb 1-5: configuration #2 chosen from 2 choices
[ 1355.302435] eth1: register 'cdc_ether' at usb-0000:00:02.0-5, CDC
Ethernet Device, 00:08:5c:57:53:b7
[ 1355.302452] usbcore: registered new interface driver cdc_ether
[ 1364.596902] eth0: no IPv6 routers present
[ 1386.273159] eth0: no IPv6 routers present
[ 1390.872042] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1390.872048] ata2.00: (BMDMA stat 0x25)
[ 1390.872054] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 1390.872055] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1390.896787] ata2.00: configured for UDMA/133
[ 1390.896797] ata2: EH complete
[ 1395.562523] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1395.562529] ata2.00: (BMDMA stat 0x25)
[ 1395.562535] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 1395.562537] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1395.584012] ata2.00: configured for UDMA/133
[ 1395.584023] ata2: EH complete
[ 1400.228010] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1400.228016] ata2.00: (BMDMA stat 0x25)
[ 1400.228022] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 1400.228024] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1400.251242] ata2.00: configured for UDMA/133
[ 1400.251254] ata2: EH complete
[ 1404.926823] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1404.926829] ata2.00: (BMDMA stat 0x25)
[ 1404.926834] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 1404.926835] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1404.950463] ata2.00: configured for UDMA/133
[ 1404.950475] ata2: EH complete
[ 1409.667289] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1409.667294] ata2.00: (BMDMA stat 0x25)
[ 1409.667300] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 1409.667302] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1409.689681] ata2.00: configured for UDMA/133
[ 1409.689692] ata2: EH complete
[ 1414.399428] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1414.399434] ata2.00: (BMDMA stat 0x25)
[ 1414.399439] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 1414.399441] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1414.420896] ata2.00: configured for UDMA/133
[ 1414.420910] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1414.420915] sd 1:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1414.420921] Descriptor sense data with sense descriptors (in hex):
[ 1414.420923] 72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[ 1414.420933] 00 00 00 84
[ 1414.420937] sd 1:0:0:0: [sda] Add. Sense: Unrecovered read error -
auto reallocate failed
[ 1414.420943] end_request: I/O error, dev sda, sector 132
[ 1414.420958] ata2: EH complete
[ 1414.421027] EXT3-fs: can't read group descriptor 7
[ 1414.422418] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 1414.423445] sd 1:0:0:0: [sda] Write Protect is off
[ 1414.423449] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1414.424675] sd 1:0:0:0: [sda] Write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[ 1414.425388] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 1414.425444] sd 1:0:0:0: [sda] Write Protect is off
[ 1414.425447] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1414.426160] sd 1:0:0:0: [sda] Write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[ 1414.584033] kjournald starting. Commit interval 5 seconds
[ 1414.584173] EXT3 FS on sda3, internal journal
[ 1414.584179] EXT3-fs: mounted filesystem with ordered data mode.
[ 2145.771299] hdb: media error (bad sector): status=0x51 { DriveReady
SeekComplete Error }
[ 2145.771306] hdb: media error (bad sector): error=0x30 {
LastFailedSense=0x03 }
[ 2145.771309] ide: failed opcode was: unknown
[ 2145.771737] hdb: error code: 0x70 sense_key: 0x03 asc: 0x10 ascq: 0x00
[ 2145.771741] end_request: I/O error, dev hdb, sector 1086708
[ 2145.771746] Buffer I/O error on device hdb, logical block 271677
[ 2145.771750] Buffer I/O error on device hdb, logical block 271678
[ 2145.771753] Buffer I/O error on device hdb, logical block 271679
[ 2145.771756] Buffer I/O error on device hdb, logical block 271680
[ 2145.771758] Buffer I/O error on device hdb, logical block 271681
[ 2145.771761] Buffer I/O error on device hdb, logical block 271682
[ 2145.771764] Buffer I/O error on device hdb, logical block 271683
[ 2145.771767] Buffer I/O error on device hdb, logical block 271684
[ 2145.771769] Buffer I/O error on device hdb, logical block 271685
[ 2145.771772] Buffer I/O error on device hdb, logical block 271686
[ 2167.051038] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2167.051043] ata2.00: (BMDMA stat 0x25)
[ 2167.051048] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 2167.051050] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 2167.076625] ata2.00: configured for UDMA/133
[ 2167.076633] ata2: EH complete
[ 2171.816500] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2171.816505] ata2.00: (BMDMA stat 0x25)
[ 2171.816511] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 2171.816512] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 2171.839842] ata2.00: configured for UDMA/133
[ 2171.839851] ata2: EH complete
[ 2176.506970] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2176.506974] ata2.00: (BMDMA stat 0x25)
[ 2176.506978] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 2176.506979] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 2176.531061] ata2.00: configured for UDMA/133
[ 2176.531066] ata2: EH complete
[ 2181.214113] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2181.214116] ata2.00: (BMDMA stat 0x25)
[ 2181.214120] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 2181.214122] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 2181.238283] ata2.00: configured for UDMA/133
[ 2181.238288] ata2: EH complete
[ 2185.937918] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2185.937921] ata2.00: (BMDMA stat 0x25)
[ 2185.937925] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 2185.937926] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 2185.961502] ata2.00: configured for UDMA/133
[ 2185.961507] ata2: EH complete
[ 2190.661734] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2190.661738] ata2.00: (BMDMA stat 0x25)
[ 2190.661743] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 2190.661744] res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 2190.684722] ata2.00: configured for UDMA/133
[ 2190.684733] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2190.684736] sd 1:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 2190.684739] Descriptor sense data with sense descriptors (in hex):
[ 2190.684741] 72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[ 2190.684746] 00 00 00 84
[ 2190.684749] sd 1:0:0:0: [sda] Add. Sense: Unrecovered read error -
auto reallocate failed
[ 2190.684753] end_request: I/O error, dev sda, sector 132
[ 2190.684765] ata2: EH complete
[ 2190.684791] EXT3-fs: can't read group descriptor 7
[ 2190.686777] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 2190.686896] sd 1:0:0:0: [sda] Write Protect is off
[ 2190.686898] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2190.687764] sd 1:0:0:0: [sda] Write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[ 2190.688180] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 2190.688390] sd 1:0:0:0: [sda] Write Protect is off
[ 2190.688392] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2190.688815] sd 1:0:0:0: [sda] Write cache: enabled, read cache:
enabled, doesn't support DPO or FUA




Used Rescue disk to start Ubuntu but cant access my sda1
Cant read the sda1 which i upgraded to hardy heron... 

plz m a newbie to ubuntu plz help :(

---

### Post by mauripop on 2008-05-14
This happened to me on a brand new Dell Inspiron 530, which came preloaded with 7.10. I upgraded to 8.04 and after rebooting I got these error messages. 

The hard disk is brand new, but I did a fsck on it anyway and it returned no errors. The 8.04 update set up GRUB with two kernels, the default 2.24-12-generic and another one, 2.22-14-generic. I tried the latter and voila, cryptic error gone and the computer booted normally. 

I am guessing then this is a seriously bitchy bug on ubuntu's 2.24 kernel. What gives? Should I file a bug report? Where?

---

### Post by Tbreezy on 2008-05-31
i just did a fresh install of ubuntu 8.04 on a dell 8100 desktop.. i got the same message...  there was a 60g hd and a 10g hd and the system had windows xp sp2 ... the 10g hd was a slave drive to the 60g..  i found some other forum sites talking about the ide port configurations of the hd's being the issue so i disconnected the 10g and then everything went fine... not sure if that helps but maybe it's a piece of the puzzle?  (this is my first post and first time with ubuntu(any linux) so i think i am way out of my technical league on this one but i enjoy the idea of open source and look forward to participating)

---

### Post by cha0s on 2008-06-01
I get this error too. As far as I know for me it's only cosmetic... I hope the disk isn't dying I just bought this notebook! ;)

---

### Post by dmb on 2008-06-07
I got something simular and i think it meant my hard drive is bad.  I'm buying a new one now, 
ubuntu@ubuntu:~/drm/linux-core$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       570146

---

### Post by toddw81 on 2008-06-23
I had the same issue and mine happened after I installed Virtual Box, I had installed the 386 modules and after that I would not boot.  I hit escape and selected the generic boot and it booted up fine.

---

