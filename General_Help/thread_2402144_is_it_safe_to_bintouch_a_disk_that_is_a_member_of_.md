---
title: "is it safe to /bin/touch a disk that is a member of raid /dev/md0"
date: 2018-09-26
forum: General Help
---

### Post by david144 on 2018-09-26
I have this hard drive which I can't tell if it's going to sleep on its own or if the hot swap enclosure is the cause of my problems but in the last 3 days its started acting up and if I re-seat the drive and run **[COLOR=#0000cd]mdadm --manage /dev/md0 --re-add /dev/sdd[/COLOR]** it rebuilds fine and works for a while.


**Is it safe to set this in cron if the drives are part of a raid array?**
```
*/5 * * * * /bin/touch /dev/sdd &>/dev/null
```


I was looking and it seems my power management are all set at 254:
```
# hdparm -I /dev/sdc | grep level
        Advanced power management level: 254
# hdparm -I /dev/sdd | grep level
        Advanced power management level: 254
# hdparm -I /dev/sde | grep level
        Advanced power management level: 254
# hdparm -I /dev/sdf | grep level
        Advanced power management level: 254

```


Here's my syslog info, let me know if there's anything relevant that I missed with grep -E "sdd|md0|ata3"
I'm hoping it's just the drive is going to sleep based on the event:
[INDENT][COLOR=#0000cd]Sep 25 13:04:02 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], is in SLEEP mode, suspending checks[/COLOR][/INDENT]

```
Sep 23 13:20:25 iSCSI-SAN kernel: [1287220.202686] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Sep 23 13:20:25 iSCSI-SAN kernel: [1287220.202696] ata3.00: failed command: FLUSH CACHE EXT
Sep 23 13:20:25 iSCSI-SAN kernel: [1287220.202709] ata3.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 18
Sep 23 13:20:25 iSCSI-SAN kernel: [1287220.202715] ata3.00: status: { DRDY }
Sep 23 13:20:25 iSCSI-SAN kernel: [1287220.202722] ata3: hard resetting link
Sep 23 13:20:35 iSCSI-SAN kernel: [1287230.202743] ata3: softreset failed (1st FIS failed)
Sep 23 13:20:35 iSCSI-SAN kernel: [1287230.202752] ata3: hard resetting link
Sep 23 13:20:45 iSCSI-SAN kernel: [1287240.202755] ata3: softreset failed (1st FIS failed)
Sep 23 13:20:45 iSCSI-SAN kernel: [1287240.202765] ata3: hard resetting link
Sep 23 13:21:20 iSCSI-SAN kernel: [1287275.203741] ata3: softreset failed (1st FIS failed)
Sep 23 13:21:20 iSCSI-SAN kernel: [1287275.203750] ata3: limiting SATA link speed to 3.0 Gbps
Sep 23 13:21:20 iSCSI-SAN kernel: [1287275.203752] ata3: hard resetting link
Sep 23 13:21:26 iSCSI-SAN kernel: [1287280.414890] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
Sep 23 13:21:26 iSCSI-SAN kernel: [1287280.414896] ata3.00: link online but device misclassified
Sep 23 13:21:31 iSCSI-SAN kernel: [1287285.454887] ata3.00: qc timeout (cmd 0xec)
Sep 23 13:21:31 iSCSI-SAN kernel: [1287285.454898] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Sep 23 13:21:31 iSCSI-SAN kernel: [1287285.454901] ata3.00: revalidation failed (errno=-5)
Sep 23 13:21:31 iSCSI-SAN kernel: [1287285.454911] ata3: hard resetting link
Sep 23 13:21:41 iSCSI-SAN kernel: [1287295.455642] ata3: softreset failed (1st FIS failed)
Sep 23 13:21:41 iSCSI-SAN kernel: [1287295.455653] ata3: hard resetting link
Sep 23 13:21:51 iSCSI-SAN kernel: [1287305.455418] ata3: softreset failed (1st FIS failed)
Sep 23 13:21:51 iSCSI-SAN kernel: [1287305.455428] ata3: hard resetting link
Sep 23 13:22:03 iSCSI-SAN kernel: [1287317.975095] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
Sep 23 13:22:08 iSCSI-SAN kernel: [1287323.087114] ata3.00: qc timeout (cmd 0x27)
Sep 23 13:22:08 iSCSI-SAN kernel: [1287323.087127] ata3.00: failed to read native max address (err_mask=0x4)
Sep 23 13:22:08 iSCSI-SAN kernel: [1287323.087129] ata3.00: HPA support seems broken, skipping HPA handling
Sep 23 13:22:08 iSCSI-SAN kernel: [1287323.087132] ata3.00: revalidation failed (errno=-5)
Sep 23 13:22:08 iSCSI-SAN kernel: [1287323.087141] ata3: limiting SATA link speed to 1.5 Gbps
Sep 23 13:22:08 iSCSI-SAN kernel: [1287323.087145] ata3: hard resetting link
Sep 23 13:22:17 iSCSI-SAN kernel: [1287331.623150] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 23 13:22:22 iSCSI-SAN kernel: [1287336.655162] ata3.00: qc timeout (cmd 0xef)
Sep 23 13:22:22 iSCSI-SAN kernel: [1287336.655175] ata3.00: failed to enable AA (error_mask=0x4)
Sep 23 13:22:22 iSCSI-SAN kernel: [1287336.655182] ata3.00: revalidation failed (errno=-5)
Sep 23 13:22:22 iSCSI-SAN kernel: [1287336.655187] ata3.00: disabled
Sep 23 13:22:22 iSCSI-SAN kernel: [1287336.655205] ata3: hard resetting link
Sep 23 13:22:32 iSCSI-SAN kernel: [1287346.655439] ata3: softreset failed (1st FIS failed)
Sep 23 13:22:32 iSCSI-SAN kernel: [1287346.655449] ata3: hard resetting link
Sep 23 13:22:39 iSCSI-SAN kernel: [1287353.295289] INFO: task md0_raid6:264 blocked for more than 120 seconds.
Sep 23 13:22:39 iSCSI-SAN kernel: [1287353.295306] md0_raid6       D    0   264      2 0x80000000
Sep 23 13:22:42 iSCSI-SAN kernel: [1287356.655656] ata3: softreset failed (1st FIS failed)
Sep 23 13:22:42 iSCSI-SAN kernel: [1287356.655665] ata3: hard resetting link
Sep 23 13:23:17 iSCSI-SAN kernel: [1287391.655350] ata3: softreset failed (1st FIS failed)
Sep 23 13:23:17 iSCSI-SAN kernel: [1287391.655361] ata3: hard resetting link
Sep 23 13:23:22 iSCSI-SAN kernel: [1287396.871454] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 23 13:23:22 iSCSI-SAN kernel: [1287396.871461] ata3.00: link online but device misclassified
Sep 23 13:23:22 iSCSI-SAN kernel: [1287396.871481] ata3: EH complete
Sep 23 13:23:22 iSCSI-SAN kernel: [1287396.871512] sd 3:0:0:0: [sdd] tag#19 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 23 13:23:22 iSCSI-SAN kernel: [1287396.871518] sd 3:0:0:0: [sdd] tag#19 CDB: Synchronize Cache(10) 35 00 00 00 00 00 00 00 00 00
Sep 23 13:23:22 iSCSI-SAN kernel: [1287396.871528] print_req_error: I/O error, dev sdd, sector 16
Sep 23 13:23:22 iSCSI-SAN kernel: [1287396.871542] md/raid:md0: Disk failure on sdd, disabling device.
Sep 23 13:23:22 iSCSI-SAN kernel: [1287396.871542] md/raid:md0: Operation continuing on 3 devices.
Sep 23 13:23:22 iSCSI-SAN kernel: [1287396.871609] sd 3:0:0:0: [sdd] tag#20 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 23 13:23:22 iSCSI-SAN kernel: [1287396.871616] sd 3:0:0:0: [sdd] tag#20 CDB: Synchronize Cache(10) 35 00 00 00 00 00 00 00 00 00
Sep 23 13:23:22 iSCSI-SAN kernel: [1287396.871621] print_req_error: I/O error, dev sdd, sector 0
Sep 24 20:50:57 iSCSI-SAN kernel: [1400652.731097] ata3: exception Emask 0x10 SAct 0x0 SErr 0x10200 action 0xe frozen
Sep 24 20:50:57 iSCSI-SAN kernel: [1400652.731104] ata3: irq_stat 0x00400000, PHY RDY changed
Sep 24 20:50:57 iSCSI-SAN kernel: [1400652.731110] ata3: SError: { Persist PHYRdyChg }
Sep 24 20:50:57 iSCSI-SAN kernel: [1400652.731151] ata3: hard resetting link
Sep 24 20:50:58 iSCSI-SAN kernel: [1400653.441431] ata3: SATA link down (SStatus 0 SControl 300)
Sep 24 20:50:58 iSCSI-SAN kernel: [1400653.441448] ata3: EH complete
Sep 24 20:50:58 iSCSI-SAN kernel: [1400653.441462] ata3.00: detaching (SCSI 3:0:0:0)
Sep 24 20:50:58 iSCSI-SAN kernel: [1400653.442491] sd 3:0:0:0: [sdd] Synchronizing SCSI cache
Sep 24 20:50:58 iSCSI-SAN kernel: [1400653.442590] sd 3:0:0:0: [sdd] Synchronize Cache(10) failed: Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 24 20:50:58 iSCSI-SAN kernel: [1400653.442594] sd 3:0:0:0: [sdd] Stopping disk
Sep 24 20:50:58 iSCSI-SAN kernel: [1400653.442622] sd 3:0:0:0: [sdd] Start/Stop Unit failed: Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 24 20:51:04 iSCSI-SAN kernel: [1400659.424427] ata3: exception Emask 0x10 SAct 0x0 SErr 0x40d0002 action 0xe frozen
Sep 24 20:51:04 iSCSI-SAN kernel: [1400659.424435] ata3: irq_stat 0x00400040, connection status changed
Sep 24 20:51:04 iSCSI-SAN kernel: [1400659.424441] ata3: SError: { RecovComm PHYRdyChg CommWake 10B8B DevExch }
Sep 24 20:51:04 iSCSI-SAN kernel: [1400659.424451] ata3: hard resetting link
Sep 24 20:51:12 iSCSI-SAN kernel: [1400667.477525] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep 24 20:51:12 iSCSI-SAN kernel: [1400667.481300] ata3.00: ATA-10: ST4000LM024-2AN17V, 0001, max UDMA/133
Sep 24 20:51:12 iSCSI-SAN kernel: [1400667.481305] ata3.00: 7814037168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Sep 24 20:51:12 iSCSI-SAN kernel: [1400667.485252] ata3.00: configured for UDMA/133
Sep 24 20:51:12 iSCSI-SAN kernel: [1400667.485266] ata3: EH complete
Sep 24 20:51:12 iSCSI-SAN kernel: [1400667.486185] sd 3:0:0:0: [sdd] 7814037168 512-byte logical blocks: (4.00 TB/3.64 TiB)
Sep 24 20:51:12 iSCSI-SAN kernel: [1400667.486190] sd 3:0:0:0: [sdd] 4096-byte physical blocks
Sep 24 20:51:12 iSCSI-SAN kernel: [1400667.486219] sd 3:0:0:0: [sdd] Write Protect is off
Sep 24 20:51:12 iSCSI-SAN kernel: [1400667.486225] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Sep 24 20:51:12 iSCSI-SAN kernel: [1400667.486283] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 24 20:51:12 iSCSI-SAN kernel: [1400667.517920] sd 3:0:0:0: [sdd] Attached SCSI disk
Sep 24 21:03:15 iSCSI-SAN smartd[6478]: Device: /dev/sdd, type changed from 'scsi' to 'sat'
Sep 24 21:03:15 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], opened
Sep 24 21:03:15 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], ST4000LM024-2AN17V, S/N:WFG05CSN, WWN:5-000c50-0ab5e59fc, FW:0001, 4.00 TB
Sep 24 21:03:15 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], not found in smartd database.
Sep 24 21:03:15 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], is SMART capable. Adding to "monitor" list.
Sep 24 21:03:37 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], state written to /var/lib/smartmontools/smartd.ST4000LM024_2AN17V-WFG05CSN.ata.state
Sep 24 21:14:33 iSCSI-SAN kernel: [1402068.320892] md: recovery of RAID array md0
Sep 24 21:33:40 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Prefailure Attribute: 1 Raw_Read_Error_Rate changed from 78 to 80
Sep 24 21:33:40 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 188 Command_Timeout changed from 97 to 100
Sep 24 21:33:40 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 195 Hardware_ECC_Recovered changed from 78 to 80
Sep 24 21:44:19 iSCSI-SAN kernel: [1403854.670493] md: md0: recovery done.
Sep 24 22:03:37 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Prefailure Attribute: 1 Raw_Read_Error_Rate changed from 80 to 81
Sep 24 22:03:37 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 70 to 69
Sep 24 22:03:37 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 30 to 31
Sep 24 22:03:37 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 195 Hardware_ECC_Recovered changed from 80 to 81
Sep 24 22:33:40 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 69 to 70
Sep 24 22:33:40 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 31 to 30
Sep 25 01:03:23 iSCSI-SAN kernel: [1415798.535982] Workqueue: xfs-sync/md0 xfs_log_worker [xfs]
Sep 25 02:03:38 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Prefailure Attribute: 1 Raw_Read_Error_Rate changed from 81 to 82
Sep 25 02:03:38 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 70 to 69
Sep 25 02:03:38 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 30 to 31
Sep 25 02:03:38 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 195 Hardware_ECC_Recovered changed from 81 to 82
Sep 25 02:33:40 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 69 to 70
Sep 25 02:33:40 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 31 to 30
Sep 25 03:33:39 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 70 to 69
Sep 25 03:33:39 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 30 to 31
Sep 25 04:03:41 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 69 to 70
Sep 25 04:03:41 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 31 to 30
Sep 25 08:03:40 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 70 to 69
Sep 25 08:03:40 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 30 to 31
Sep 25 09:03:39 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 69 to 70
Sep 25 09:03:39 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 31 to 30
Sep 25 10:33:37 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Prefailure Attribute: 1 Raw_Read_Error_Rate changed from 82 to 83
Sep 25 10:33:37 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 195 Hardware_ECC_Recovered changed from 82 to 83
Sep 25 13:00:23 iSCSI-SAN kernel: [1458819.128641] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Sep 25 13:00:23 iSCSI-SAN kernel: [1458819.128650] ata3.00: failed command: FLUSH CACHE EXT
Sep 25 13:00:23 iSCSI-SAN kernel: [1458819.128663] ata3.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 7
Sep 25 13:00:23 iSCSI-SAN kernel: [1458819.128670] ata3.00: status: { DRDY }
Sep 25 13:00:23 iSCSI-SAN kernel: [1458819.128677] ata3: hard resetting link
Sep 25 13:00:33 iSCSI-SAN kernel: [1458829.128707] ata3: softreset failed (1st FIS failed)
Sep 25 13:00:33 iSCSI-SAN kernel: [1458829.128717] ata3: hard resetting link
Sep 25 13:00:43 iSCSI-SAN kernel: [1458839.129350] ata3: softreset failed (1st FIS failed)
Sep 25 13:00:43 iSCSI-SAN kernel: [1458839.129360] ata3: hard resetting link
Sep 25 13:00:54 iSCSI-SAN kernel: [1458849.436844] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep 25 13:00:59 iSCSI-SAN kernel: [1458854.684871] ata3.00: qc timeout (cmd 0x27)
Sep 25 13:00:59 iSCSI-SAN kernel: [1458854.684883] ata3.00: failed to read native max address (err_mask=0x4)
Sep 25 13:00:59 iSCSI-SAN kernel: [1458854.684885] ata3.00: HPA support seems broken, skipping HPA handling
Sep 25 13:00:59 iSCSI-SAN kernel: [1458854.684888] ata3.00: revalidation failed (errno=-5)
Sep 25 13:00:59 iSCSI-SAN kernel: [1458854.684897] ata3: hard resetting link
Sep 25 13:01:09 iSCSI-SAN kernel: [1458864.685409] ata3: softreset failed (1st FIS failed)
Sep 25 13:01:09 iSCSI-SAN kernel: [1458864.685419] ata3: hard resetting link
Sep 25 13:01:19 iSCSI-SAN kernel: [1458874.685597] ata3: softreset failed (1st FIS failed)
Sep 25 13:01:19 iSCSI-SAN kernel: [1458874.685607] ata3: hard resetting link
Sep 25 13:01:54 iSCSI-SAN kernel: [1458909.685241] ata3: softreset failed (1st FIS failed)
Sep 25 13:01:54 iSCSI-SAN kernel: [1458909.685251] ata3: limiting SATA link speed to 3.0 Gbps
Sep 25 13:01:54 iSCSI-SAN kernel: [1458909.685254] ata3: hard resetting link
Sep 25 13:01:59 iSCSI-SAN kernel: [1458914.901249] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
Sep 25 13:01:59 iSCSI-SAN kernel: [1458914.901255] ata3.00: link online but device misclassified
Sep 25 13:02:04 iSCSI-SAN kernel: [1458919.965254] ata3.00: qc timeout (cmd 0xec)
Sep 25 13:02:04 iSCSI-SAN kernel: [1458919.965264] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Sep 25 13:02:04 iSCSI-SAN kernel: [1458919.965267] ata3.00: revalidation failed (errno=-5)
Sep 25 13:02:04 iSCSI-SAN kernel: [1458919.965275] ata3: limiting SATA link speed to 1.5 Gbps
Sep 25 13:02:04 iSCSI-SAN kernel: [1458919.965280] ata3: hard resetting link
Sep 25 13:02:14 iSCSI-SAN kernel: [1458929.965577] ata3: softreset failed (1st FIS failed)
Sep 25 13:02:14 iSCSI-SAN kernel: [1458929.965587] ata3: hard resetting link
Sep 25 13:02:20 iSCSI-SAN kernel: [1458935.837372] INFO: task md0_raid6:264 blocked for more than 120 seconds.
Sep 25 13:02:20 iSCSI-SAN kernel: [1458935.837388] md0_raid6       D    0   264      2 0x80000000
Sep 25 13:02:20 iSCSI-SAN kernel: [1458935.837511] INFO: task xfsaild/md0:725 blocked for more than 120 seconds.
Sep 25 13:02:20 iSCSI-SAN kernel: [1458935.837521] xfsaild/md0     D    0   725      2 0x80000000
Sep 25 13:02:20 iSCSI-SAN kernel: [1458935.838060] Workqueue: xfs-sync/md0 xfs_log_worker [xfs]
Sep 25 13:02:24 iSCSI-SAN kernel: [1458939.966277] ata3: softreset failed (1st FIS failed)
Sep 25 13:02:24 iSCSI-SAN kernel: [1458939.966287] ata3: hard resetting link
Sep 25 13:02:59 iSCSI-SAN kernel: [1458974.965584] ata3: softreset failed (1st FIS failed)
Sep 25 13:02:59 iSCSI-SAN kernel: [1458974.965596] ata3: hard resetting link
Sep 25 13:03:04 iSCSI-SAN kernel: [1458980.181641] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 25 13:03:04 iSCSI-SAN kernel: [1458980.181647] ata3.00: link online but device misclassified
Sep 25 13:03:15 iSCSI-SAN kernel: [1458990.365703] ata3.00: qc timeout (cmd 0xec)
Sep 25 13:03:15 iSCSI-SAN kernel: [1458990.365713] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Sep 25 13:03:15 iSCSI-SAN kernel: [1458990.365716] ata3.00: revalidation failed (errno=-5)
Sep 25 13:03:15 iSCSI-SAN kernel: [1458990.365724] ata3.00: disabled
Sep 25 13:03:15 iSCSI-SAN kernel: [1458990.365742] ata3: hard resetting link
Sep 25 13:03:25 iSCSI-SAN kernel: [1459000.365705] ata3: softreset failed (1st FIS failed)
Sep 25 13:03:25 iSCSI-SAN kernel: [1459000.365715] ata3: hard resetting link
Sep 25 13:03:35 iSCSI-SAN kernel: [1459010.366018] ata3: softreset failed (1st FIS failed)
Sep 25 13:03:35 iSCSI-SAN kernel: [1459010.366028] ata3: hard resetting link
Sep 25 13:04:02 iSCSI-SAN kernel: [1459038.086012] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 25 13:04:02 iSCSI-SAN kernel: [1459038.086035] ata3: EH complete
Sep 25 13:04:02 iSCSI-SAN kernel: [1459038.086084] sd 3:0:0:0: [sdd] tag#8 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 13:04:02 iSCSI-SAN kernel: [1459038.086091] sd 3:0:0:0: [sdd] tag#8 CDB: Synchronize Cache(10) 35 00 00 00 00 00 00 00 00 00
Sep 25 13:04:02 iSCSI-SAN kernel: [1459038.086103] print_req_error: I/O error, dev sdd, sector 16
Sep 25 13:04:02 iSCSI-SAN kernel: [1459038.086122] md/raid:md0: Disk failure on sdd, disabling device.
Sep 25 13:04:02 iSCSI-SAN kernel: [1459038.086122] md/raid:md0: Operation continuing on 3 devices.
Sep 25 13:04:02 iSCSI-SAN kernel: [1459038.086218] sd 3:0:0:0: [sdd] tag#9 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 13:04:02 iSCSI-SAN kernel: [1459038.086224] sd 3:0:0:0: [sdd] tag#9 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 25 13:04:02 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], is in SLEEP mode, suspending checks
Sep 25 13:33:37 iSCSI-SAN kernel: [1460813.299179] sd 3:0:0:0: [sdd] tag#11 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 13:33:37 iSCSI-SAN kernel: [1460813.299186] sd 3:0:0:0: [sdd] tag#11 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 25 14:03:37 iSCSI-SAN kernel: [1462613.033739] sd 3:0:0:0: [sdd] tag#13 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 14:03:37 iSCSI-SAN kernel: [1462613.033747] sd 3:0:0:0: [sdd] tag#13 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 25 14:33:37 iSCSI-SAN kernel: [1464413.028741] sd 3:0:0:0: [sdd] tag#15 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 14:33:37 iSCSI-SAN kernel: [1464413.028749] sd 3:0:0:0: [sdd] tag#15 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 25 15:03:37 iSCSI-SAN kernel: [1466212.612314] sd 3:0:0:0: [sdd] tag#17 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 15:03:37 iSCSI-SAN kernel: [1466212.612322] sd 3:0:0:0: [sdd] tag#17 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 25 15:33:37 iSCSI-SAN kernel: [1468013.031358] sd 3:0:0:0: [sdd] tag#19 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 15:33:37 iSCSI-SAN kernel: [1468013.031367] sd 3:0:0:0: [sdd] tag#19 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 25 16:03:37 iSCSI-SAN kernel: [1469812.679720] sd 3:0:0:0: [sdd] tag#21 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 16:03:37 iSCSI-SAN kernel: [1469812.679728] sd 3:0:0:0: [sdd] tag#21 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 25 16:33:37 iSCSI-SAN kernel: [1471613.272187] sd 3:0:0:0: [sdd] tag#23 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 16:33:37 iSCSI-SAN kernel: [1471613.272195] sd 3:0:0:0: [sdd] tag#23 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 25 17:03:38 iSCSI-SAN kernel: [1473413.549843] sd 3:0:0:0: [sdd] tag#25 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 17:03:38 iSCSI-SAN kernel: [1473413.549851] sd 3:0:0:0: [sdd] tag#25 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 25 17:33:37 iSCSI-SAN kernel: [1475213.219783] sd 3:0:0:0: [sdd] tag#27 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 17:33:37 iSCSI-SAN kernel: [1475213.219791] sd 3:0:0:0: [sdd] tag#27 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 25 18:03:37 iSCSI-SAN kernel: [1477012.683379] sd 3:0:0:0: [sdd] tag#29 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 18:03:37 iSCSI-SAN kernel: [1477012.683387] sd 3:0:0:0: [sdd] tag#29 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 25 18:33:37 iSCSI-SAN kernel: [1478813.091016] sd 3:0:0:0: [sdd] tag#0 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 18:33:37 iSCSI-SAN kernel: [1478813.091024] sd 3:0:0:0: [sdd] tag#0 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 25 19:03:37 iSCSI-SAN kernel: [1480612.956241] sd 3:0:0:0: [sdd] tag#2 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 19:03:37 iSCSI-SAN kernel: [1480612.956250] sd 3:0:0:0: [sdd] tag#2 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 25 19:33:37 iSCSI-SAN kernel: [1482413.472596] sd 3:0:0:0: [sdd] tag#4 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 19:33:37 iSCSI-SAN kernel: [1482413.472605] sd 3:0:0:0: [sdd] tag#4 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 25 20:03:37 iSCSI-SAN kernel: [1484213.077286] sd 3:0:0:0: [sdd] tag#6 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 20:03:37 iSCSI-SAN kernel: [1484213.077296] sd 3:0:0:0: [sdd] tag#6 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 25 20:33:39 iSCSI-SAN kernel: [1486014.928517] sd 3:0:0:0: [sdd] tag#8 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 20:33:39 iSCSI-SAN kernel: [1486014.928527] sd 3:0:0:0: [sdd] tag#8 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 25 21:03:37 iSCSI-SAN kernel: [1487813.220068] sd 3:0:0:0: [sdd] tag#10 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 21:03:37 iSCSI-SAN kernel: [1487813.220076] sd 3:0:0:0: [sdd] tag#10 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 25 21:33:37 iSCSI-SAN kernel: [1489613.009181] sd 3:0:0:0: [sdd] tag#12 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 21:33:37 iSCSI-SAN kernel: [1489613.009189] sd 3:0:0:0: [sdd] tag#12 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 25 22:03:37 iSCSI-SAN kernel: [1491413.373420] sd 3:0:0:0: [sdd] tag#14 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 22:03:37 iSCSI-SAN kernel: [1491413.373430] sd 3:0:0:0: [sdd] tag#14 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 25 22:33:37 iSCSI-SAN kernel: [1493213.032416] sd 3:0:0:0: [sdd] tag#16 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 22:33:37 iSCSI-SAN kernel: [1493213.032426] sd 3:0:0:0: [sdd] tag#16 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 25 23:03:37 iSCSI-SAN kernel: [1495013.505390] sd 3:0:0:0: [sdd] tag#18 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 23:03:37 iSCSI-SAN kernel: [1495013.505398] sd 3:0:0:0: [sdd] tag#18 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 25 23:33:37 iSCSI-SAN kernel: [1496813.066750] sd 3:0:0:0: [sdd] tag#20 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 25 23:33:37 iSCSI-SAN kernel: [1496813.066760] sd 3:0:0:0: [sdd] tag#20 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 26 00:03:37 iSCSI-SAN kernel: [1498612.823350] sd 3:0:0:0: [sdd] tag#22 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 00:03:37 iSCSI-SAN kernel: [1498612.823358] sd 3:0:0:0: [sdd] tag#22 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 26 00:33:37 iSCSI-SAN kernel: [1500413.220108] sd 3:0:0:0: [sdd] tag#24 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 00:33:37 iSCSI-SAN kernel: [1500413.220115] sd 3:0:0:0: [sdd] tag#24 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 26 01:03:37 iSCSI-SAN kernel: [1502213.486604] sd 3:0:0:0: [sdd] tag#26 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 01:03:37 iSCSI-SAN kernel: [1502213.486612] sd 3:0:0:0: [sdd] tag#26 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 26 01:33:37 iSCSI-SAN kernel: [1504013.558636] sd 3:0:0:0: [sdd] tag#28 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 01:33:37 iSCSI-SAN kernel: [1504013.558643] sd 3:0:0:0: [sdd] tag#28 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 26 02:01:07 iSCSI-SAN kernel: [1505662.906047] sd 3:0:0:0: [sdd] tag#30 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 02:01:07 iSCSI-SAN kernel: [1505662.906055] sd 3:0:0:0: [sdd] tag#30 CDB: Read(16) 88 00 00 00 00 01 d1 c0 be 00 00 00 00 08 00 00
Sep 26 02:01:07 iSCSI-SAN kernel: [1505662.906058] print_req_error: I/O error, dev sdd, sector 7814036992
Sep 26 02:01:07 iSCSI-SAN kernel: [1505662.906247] sd 3:0:0:0: [sdd] tag#0 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 02:01:07 iSCSI-SAN kernel: [1505662.906255] sd 3:0:0:0: [sdd] tag#0 CDB: Read(16) 88 00 00 00 00 01 d1 c0 be a0 00 00 00 08 00 00
Sep 26 02:01:07 iSCSI-SAN kernel: [1505662.906259] print_req_error: I/O error, dev sdd, sector 7814037152
Sep 26 02:01:07 iSCSI-SAN kernel: [1505662.906326] sd 3:0:0:0: [sdd] tag#1 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 02:01:07 iSCSI-SAN kernel: [1505662.906331] sd 3:0:0:0: [sdd] tag#1 CDB: Read(16) 88 00 00 00 00 01 d1 c0 be af 00 00 00 01 00 00
Sep 26 02:01:07 iSCSI-SAN kernel: [1505662.906333] print_req_error: I/O error, dev sdd, sector 7814037167
Sep 26 02:01:07 iSCSI-SAN kernel: [1505662.906399] sd 3:0:0:0: [sdd] tag#2 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 02:01:07 iSCSI-SAN kernel: [1505662.906404] sd 3:0:0:0: [sdd] tag#2 CDB: Read(16) 88 00 00 00 00 01 d1 c0 be ae 00 00 00 01 00 00
Sep 26 02:01:07 iSCSI-SAN kernel: [1505662.906406] print_req_error: I/O error, dev sdd, sector 7814037166
Sep 26 02:01:07 iSCSI-SAN kernel: [1505662.906464] sd 3:0:0:0: [sdd] tag#3 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 02:01:07 iSCSI-SAN kernel: [1505662.906481] sd 3:0:0:0: [sdd] tag#3 CDB: Read(16) 88 00 00 00 00 00 00 00 00 00 00 00 00 01 00 00
Sep 26 02:01:07 iSCSI-SAN kernel: [1505662.906493] print_req_error: I/O error, dev sdd, sector 0
Sep 26 02:01:07 iSCSI-SAN kernel: [1505662.906579] sd 3:0:0:0: [sdd] tag#4 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 02:01:07 iSCSI-SAN kernel: [1505662.906586] sd 3:0:0:0: [sdd] tag#4 CDB: Read(16) 88 00 00 00 00 00 00 00 00 00 00 00 00 01 00 00
Sep 26 02:01:07 iSCSI-SAN kernel: [1505662.906589] print_req_error: I/O error, dev sdd, sector 0
Sep 26 02:03:37 iSCSI-SAN kernel: [1505813.119856] sd 3:0:0:0: [sdd] tag#15 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 02:03:37 iSCSI-SAN kernel: [1505813.119865] sd 3:0:0:0: [sdd] tag#15 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 26 02:33:37 iSCSI-SAN kernel: [1507613.581669] sd 3:0:0:0: [sdd] tag#17 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 02:33:37 iSCSI-SAN kernel: [1507613.581677] sd 3:0:0:0: [sdd] tag#17 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 26 03:03:37 iSCSI-SAN kernel: [1509413.218702] sd 3:0:0:0: [sdd] tag#19 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 03:03:37 iSCSI-SAN kernel: [1509413.218711] sd 3:0:0:0: [sdd] tag#19 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 26 03:33:37 iSCSI-SAN kernel: [1511213.637109] sd 3:0:0:0: [sdd] tag#21 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 03:33:37 iSCSI-SAN kernel: [1511213.637117] sd 3:0:0:0: [sdd] tag#21 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 26 04:03:37 iSCSI-SAN kernel: [1513013.165762] sd 3:0:0:0: [sdd] tag#23 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 04:03:37 iSCSI-SAN kernel: [1513013.165770] sd 3:0:0:0: [sdd] tag#23 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 26 04:33:37 iSCSI-SAN kernel: [1514813.606084] sd 3:0:0:0: [sdd] tag#25 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 04:33:37 iSCSI-SAN kernel: [1514813.606091] sd 3:0:0:0: [sdd] tag#25 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 26 05:03:37 iSCSI-SAN kernel: [1516613.221375] sd 3:0:0:0: [sdd] tag#27 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 05:03:37 iSCSI-SAN kernel: [1516613.221383] sd 3:0:0:0: [sdd] tag#27 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 26 05:33:37 iSCSI-SAN kernel: [1518413.075438] sd 3:0:0:0: [sdd] tag#29 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 05:33:37 iSCSI-SAN kernel: [1518413.075445] sd 3:0:0:0: [sdd] tag#29 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 26 06:03:38 iSCSI-SAN kernel: [1520213.797718] sd 3:0:0:0: [sdd] tag#0 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 06:03:38 iSCSI-SAN kernel: [1520213.797728] sd 3:0:0:0: [sdd] tag#0 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 26 06:33:37 iSCSI-SAN kernel: [1522013.521668] sd 3:0:0:0: [sdd] tag#2 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 06:33:37 iSCSI-SAN kernel: [1522013.521675] sd 3:0:0:0: [sdd] tag#2 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 26 07:03:37 iSCSI-SAN kernel: [1523813.397409] sd 3:0:0:0: [sdd] tag#4 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 07:03:37 iSCSI-SAN kernel: [1523813.397417] sd 3:0:0:0: [sdd] tag#4 CDB: ATA command pass through(16) 85 06 2c 00 00 00 00 00 00 00 00 00 00 00 e5 00
Sep 26 07:12:54 iSCSI-SAN kernel: [1524370.341341] ata3: exception Emask 0x10 SAct 0x0 SErr 0x10200 action 0xe frozen
Sep 26 07:12:54 iSCSI-SAN kernel: [1524370.341349] ata3: irq_stat 0x00400000, PHY RDY changed
Sep 26 07:12:54 iSCSI-SAN kernel: [1524370.341355] ata3: SError: { Persist PHYRdyChg }
Sep 26 07:12:54 iSCSI-SAN kernel: [1524370.341365] ata3: hard resetting link
Sep 26 07:12:55 iSCSI-SAN kernel: [1524371.051972] ata3: SATA link down (SStatus 0 SControl 300)
Sep 26 07:12:55 iSCSI-SAN kernel: [1524371.051987] ata3: EH complete
Sep 26 07:12:55 iSCSI-SAN kernel: [1524371.052008] ata3.00: detaching (SCSI 3:0:0:0)
Sep 26 07:12:55 iSCSI-SAN kernel: [1524371.053111] sd 3:0:0:0: [sdd] Synchronizing SCSI cache
Sep 26 07:12:55 iSCSI-SAN kernel: [1524371.053189] sd 3:0:0:0: [sdd] Synchronize Cache(10) failed: Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 07:12:55 iSCSI-SAN kernel: [1524371.053192] sd 3:0:0:0: [sdd] Stopping disk
Sep 26 07:12:55 iSCSI-SAN kernel: [1524371.053210] sd 3:0:0:0: [sdd] Start/Stop Unit failed: Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 26 07:13:11 iSCSI-SAN kernel: [1524387.382787] ata3: exception Emask 0x10 SAct 0x0 SErr 0x40d0002 action 0xe frozen
Sep 26 07:13:11 iSCSI-SAN kernel: [1524387.382796] ata3: irq_stat 0x00400040, connection status changed
Sep 26 07:13:11 iSCSI-SAN kernel: [1524387.382802] ata3: SError: { RecovComm PHYRdyChg CommWake 10B8B DevExch }
Sep 26 07:13:11 iSCSI-SAN kernel: [1524387.382812] ata3: hard resetting link
Sep 26 07:13:19 iSCSI-SAN kernel: [1524394.956127] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep 26 07:13:19 iSCSI-SAN kernel: [1524394.959936] ata3.00: ATA-10: ST4000LM024-2AN17V, 0001, max UDMA/133
Sep 26 07:13:19 iSCSI-SAN kernel: [1524394.959942] ata3.00: 7814037168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Sep 26 07:13:19 iSCSI-SAN kernel: [1524394.963775] ata3.00: configured for UDMA/133
Sep 26 07:13:19 iSCSI-SAN kernel: [1524394.963789] ata3: EH complete
Sep 26 07:13:19 iSCSI-SAN kernel: [1524394.964670] sd 3:0:0:0: [sdd] 7814037168 512-byte logical blocks: (4.00 TB/3.64 TiB)
Sep 26 07:13:19 iSCSI-SAN kernel: [1524394.964676] sd 3:0:0:0: [sdd] 4096-byte physical blocks
Sep 26 07:13:19 iSCSI-SAN kernel: [1524394.964720] sd 3:0:0:0: [sdd] Write Protect is off
Sep 26 07:13:19 iSCSI-SAN kernel: [1524394.964724] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Sep 26 07:13:19 iSCSI-SAN kernel: [1524394.964804] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 26 07:13:19 iSCSI-SAN kernel: [1524394.996489] sd 3:0:0:0: [sdd] Attached SCSI disk
Sep 26 07:17:02 iSCSI-SAN kernel: [1524618.129448] md: recovery of RAID array md0
Sep 26 07:33:43 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], is back in ACTIVE or IDLE mode, resuming checks (37 checks skipped)
Sep 26 07:33:45 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Prefailure Attribute: 1 Raw_Read_Error_Rate changed from 83 to 84
Sep 26 07:33:45 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 183 Runtime_Bad_Block changed from 98 to 97
Sep 26 07:33:45 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 70 to 69
Sep 26 07:33:45 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 30 to 31
Sep 26 07:33:45 iSCSI-SAN smartd[6478]: Device: /dev/sdd [SAT], SMART Usage Attribute: 195 Hardware_ECC_Recovered changed from 83 to 84

```

---

### Post by TheFu on 2018-09-26
Looks like a failing cable, bad sata port or some other important, data corruption issue.  Try reseating all the cables as a first step. Both sides.

---

