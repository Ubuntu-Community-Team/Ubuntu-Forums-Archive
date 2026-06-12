---
title: "BTRFS RAID 5 on LUKS failure"
date: 2020-02-24
forum: General Help
---

### Post by BatteryKing on 2020-02-24
OS: Ubuntu Mate 18.04

So one thing I am testing out is how to have full drive encryption with BTRFS RAID 5 for offline backup purposes (where the data at rest part of full drive encryption can be really handy).  One path I tried was to write a script to take one passphrase and give it to the LUKS partition on all of the drives and then do a BTRFS RAID 5 on top.  The reason I am not doing the RAID with MD RAID is after a single loss of power due to a loose fitting power cord right after moving, it was complaining about a bad or missing superblock and nothing I tried would correct the issue, causing complete loss of the backup array.  (Fortunately the sources held together despite the backup failing and I had a second backup just for such occasions.)  The reason I am not using my hardware controller is after a single drive failure while the drives were out of the system, the hardware RAID controller, Avago MegaRAID 9361-8i, wiped out all of the data on all of the drives when I tried to remount them.  (At least with the hardware RAID controller I have never lost an array when the problem happened while the drives were inside the system and mounted by the RAID controller.)  The reason I am not using OpenZFS 8.x, especially as this has built in encryption is in my tests it caused something to go wrong in the kernel, leading Xorg to crash when I tried to do a large copy to an OpenZFS array.  (This problem has been replicated exactly on other systems with the same write test.)

So now trying BTRFS RAID 5 on on LUKS, however a single read error left the drive in question in a wedged state where it just reported to syslog on every single I/O operation (I was diffing over 1TB of files to make sure they copied over correctly) that it cannot remap the bad sector.  I looked at the SMART data and this is the only error on the drive.  I noticed no more I/O happens to the drive after this error, just lots and lots and lots of error messages to syslog.

Here is device status information from btrfs:
```

root@tick:~/scripts# btrfs device stats /mnt/test2                                                                                                                                                                                                                             
[/dev/mapper/test2-1_luks].write_io_errs    3479812                                                                                                                                                                                                                            
[/dev/mapper/test2-1_luks].read_io_errs     3701364                                                                                                                                                                                                                            
[/dev/mapper/test2-1_luks].flush_io_errs    1                                                                                                                                                                                                                                  
[/dev/mapper/test2-1_luks].corruption_errs  0                                                                                                                                                                                                                                  
[/dev/mapper/test2-1_luks].generation_errs  0                                                                                                                                                                                                                                  
[/dev/mapper/test2-2_luks].write_io_errs    0                                                                                                                                                                                                                                  
[/dev/mapper/test2-2_luks].read_io_errs     0                                                                                                                                                                                                                                  
[/dev/mapper/test2-2_luks].flush_io_errs    0                                                                                                                                                                                                                                  
[/dev/mapper/test2-2_luks].corruption_errs  0                                                                                                                                                                                                                                  
[/dev/mapper/test2-2_luks].generation_errs  0                                                                                                                                                                                                                                  
[/dev/mapper/test2-3_luks].write_io_errs    0                                                                                                                                                                                                                                  
[/dev/mapper/test2-3_luks].read_io_errs     0                                                                                                                                                                                                                                  
[/dev/mapper/test2-3_luks].flush_io_errs    0                                                                                                                                                                                                                                  
[/dev/mapper/test2-3_luks].corruption_errs  0                                                                                                                                                                                                                                  
[/dev/mapper/test2-3_luks].generation_errs  0                                                                                                                                                                                                                                  
[/dev/mapper/test2-4_luks].write_io_errs    0                                                                                                                                                                                                                                  
[/dev/mapper/test2-4_luks].read_io_errs     0                                                                                                                                                                                                                                  
[/dev/mapper/test2-4_luks].flush_io_errs    0                                                                                                                                                                                                                                  
[/dev/mapper/test2-4_luks].corruption_errs  0                                                                                                                                                                                                                                  
[/dev/mapper/test2-4_luks].generation_errs  0                                                                                                                                                                                                                                  
root@tick:~/scripts# btrfs device stats /dev/mapper/test2-1_luks                                                                                                                                                                                                               
[/dev/mapper/test2-1_luks].write_io_errs    3622990                                                                                                                                                                                                                            
[/dev/mapper/test2-1_luks].read_io_errs     3853315                                                                                                                                                                                                                            
[/dev/mapper/test2-1_luks].flush_io_errs    1                                                                                                                                                                                                                                  
[/dev/mapper/test2-1_luks].corruption_errs  0                                                                                                                                                                                                                                  
[/dev/mapper/test2-1_luks].generation_errs  0                                                                                                                                                                                                                                  

```

Here is the SMART data from the affected drive:
```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       1
  3 Spin_Up_Time            0x0027   186   148   021    Pre-fail  Always       -       9666
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       40
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       1849
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       40
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       31
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       8
194 Temperature_Celsius     0x0022   113   108   000    Old_age   Always       -       39
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       1

```

Here is the most repeated line in my now multi-GB syslog file:
```

Feb 24 10:03:57 tick kernel: [565199.749173] blk_partition_remap: fail for partition 1

```

I am thinking I am going to have to drop the encryption layer between BTRFS and the physical drives.  Will update on the workaround.

---

