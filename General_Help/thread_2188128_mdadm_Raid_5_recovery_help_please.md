---
title: "mdadm Raid 5 recovery help please"
date: 2013-11-15
forum: General Help
---

### Post by mshogg on 2013-11-15
Hi All

I know there are a lot of posts on this subject and i think i have read them all but i still cant fix my problem.

I am running Ubuntu from a USB stick and have 6 x 3TB drives in a Raid 5.

One day last week, I powered on the machine and it didnt boot into the gui, instead it booted to the initramfs prompt. After following some guides on here i found out that a drive had failed, so i powered down, removed the drive, replaced with an identical new drive and powered back up.

I dont know if i use the mdadm commands at the initramfs prompt, or boot into manual or even Ubuntu gui and then run a terminal session. I have tried all 3 and they seem to give me a different response depends on where i run them.

I have tried assemble, with force, scan, sometimes my 6th drive is detected as sdf sometimes it isnt present at all. I did notice that the sdd drive have a few errors in SMART but its still green and healthy it says.

anyway, i am a complete n00b to this, i just managed to get the raid 5 setup and have never used linux before now, if anyone could help me I would greatly appreciate it as stupidly i dont have any backups, as i thought raid 5 was enough :o( i wont make that mistake angain.

thanks in advance

Michael

---

### Post by SaturnusDJ on 2013-11-15
If you've read a lot about this you know we need the examine outputs for all the members.

```

mdadm --examine /dev/sda1

```

S.M.A.R.T. outputs of all members would be good too.
```
smartctl -a /dev/sda
```

---

### Post by mshogg on 2013-11-15
Hi SaturnusDJ

Thanks for replying, yes i can get you those but i dont know where i run it from, do i run it from:-

initramfs prompt
root@proliant prompt
or skip mounting and boot fully into Ubuntu gui and open a UXterm/XTerm session

or does it not matter which one please?

thanks

---

### Post by SaturnusDJ on 2013-11-15
The information should be the same from all methods.

---

### Post by mshogg on 2013-11-15
Hi

I ran these from the XTerm session, sdf says no supoerblocks (this is the new drive)

/dev/sda:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x3
     Array UUID : cb39f990:2e3f054c:73624174:a29f8aae
           Name : proliant:0  (local to host proliant)
  Creation Time : Tue Oct 23 12:12:32 2012
     Raid Level : raid5
   Raid Devices : 6


 Avail Dev Size : 5860531120 (2794.52 GiB 3000.59 GB)
     Array Size : 29302654080 (13972.59 GiB 15002.96 GB)
  Used Dev Size : 5860530816 (2794.52 GiB 3000.59 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
Recovery Offset : 23766016 sectors
          State : clean
    Device UUID : 060426e7:0142a39a:72c8be59:cc246c3a


Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Nov 11 22:16:01 2013
       Checksum : fe234fd2 - correct
         Events : 126796


         Layout : left-symmetric
     Chunk Size : 64K


   Device Role : Active device 0
   Array State : AAAAA. ('A' == active, '.' == missing)

/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : cb39f990:2e3f054c:73624174:a29f8aae
           Name : proliant:0  (local to host proliant)
  Creation Time : Tue Oct 23 12:12:32 2012
     Raid Level : raid5
   Raid Devices : 6


 Avail Dev Size : 5860531120 (2794.52 GiB 3000.59 GB)
     Array Size : 29302654080 (13972.59 GiB 15002.96 GB)
  Used Dev Size : 5860530816 (2794.52 GiB 3000.59 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 0c7e3646:65476908:64245949:1b39050b


Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Nov 11 22:16:01 2013
       Checksum : 89c29b7b - correct
         Events : 126796


         Layout : left-symmetric
     Chunk Size : 64K


   Device Role : Active device 1
   Array State : AAAAA. ('A' == active, '.' == missing)

/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : cb39f990:2e3f054c:73624174:a29f8aae
           Name : proliant:0  (local to host proliant)
  Creation Time : Tue Oct 23 12:12:32 2012
     Raid Level : raid5
   Raid Devices : 6


 Avail Dev Size : 5860531120 (2794.52 GiB 3000.59 GB)
     Array Size : 29302654080 (13972.59 GiB 15002.96 GB)
  Used Dev Size : 5860530816 (2794.52 GiB 3000.59 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : a4256fb7:a4a571f3:0cf5af02:633246ba


Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Nov 11 22:16:01 2013
       Checksum : 4e9b6b45 - correct
         Events : 126796


         Layout : left-symmetric
     Chunk Size : 64K


   Device Role : Active device 2
   Array State : AAAAA. ('A' == active, '.' == missing)

/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : cb39f990:2e3f054c:73624174:a29f8aae
           Name : proliant:0  (local to host proliant)
  Creation Time : Tue Oct 23 12:12:32 2012
     Raid Level : raid5
   Raid Devices : 6


 Avail Dev Size : 5860531120 (2794.52 GiB 3000.59 GB)
     Array Size : 29302654080 (13972.59 GiB 15002.96 GB)
  Used Dev Size : 5860530816 (2794.52 GiB 3000.59 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 0609fe4a:1d57d31f:e5618980:18881091


Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Nov 11 22:16:01 2013
       Checksum : 632fc2ae - correct
         Events : 126796


         Layout : left-symmetric
     Chunk Size : 64K


   Device Role : Active device 3
   Array State : AAAAA. ('A' == active, '.' == missing)

/dev/sde:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : cb39f990:2e3f054c:73624174:a29f8aae
           Name : proliant:0  (local to host proliant)
  Creation Time : Tue Oct 23 12:12:32 2012
     Raid Level : raid5
   Raid Devices : 6


 Avail Dev Size : 5860531120 (2794.52 GiB 3000.59 GB)
     Array Size : 29302654080 (13972.59 GiB 15002.96 GB)
  Used Dev Size : 5860530816 (2794.52 GiB 3000.59 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : fb9f2b5c:356c1ef3:14a27d62:8288b98d


Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Nov 11 22:16:01 2013
       Checksum : 2645af56 - correct
         Events : 126796


         Layout : left-symmetric
     Chunk Size : 64K


   Device Role : Active device 4
   Array State : AAAAA. ('A' == active, '.' == missing)

thanks

---

### Post by mshogg on 2013-11-15
smarctl output as follows

smartctl 5.41 2011-06-09 r3365 [i686-linux-3.0.0-30-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)


=== START OF INFORMATION SECTION ===
Device Model:     ST3000DM001-9YN166
Serial Number:    W1F0QTV8
LU WWN Device Id: 5 000c50 05173ab22
Firmware Version: CC9F
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Fri Nov 15 18:05:55 2013 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(  584) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x3081)	SCT Status supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   119   099   006    Pre-fail  Always       -       204668792
  3 Spin_Up_Time            0x0003   094   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       230
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   075   060   030    Pre-fail  Always       -       38277857
  9 Power_On_Hours          0x0032   089   089   000    Old_age   Always       -       10123
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       229
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   099   000    Old_age   Always       -       1
189 High_Fly_Writes         0x003a   098   098   000    Old_age   Always       -       2
190 Airflow_Temperature_Cel 0x0022   064   057   045    Old_age   Always       -       36 (Min/Max 22/36)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       128
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       490
194 Temperature_Celsius     0x0022   036   043   000    Old_age   Always       -       36 (0 21 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       172949743085441
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       10771140059
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       77573466169074


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      1068         -
# 2  Extended offline    Aborted by host               90%       952         -


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


smartctl 5.41 2011-06-09 r3365 [i686-linux-3.0.0-30-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)


=== START OF INFORMATION SECTION ===
Device Model:     ST3000DM001-9YN166
Serial Number:    W1F0RN1Y
LU WWN Device Id: 5 000c50 051747423
Firmware Version: CC9F
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Fri Nov 15 18:06:11 2013 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(  575) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x3081)	SCT Status supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   114   099   006    Pre-fail  Always       -       60263880
  3 Spin_Up_Time            0x0003   094   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       251
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   075   060   030    Pre-fail  Always       -       37869746
  9 Power_On_Hours          0x0032   089   089   000    Old_age   Always       -       10158
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       251
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   063   055   045    Old_age   Always       -       37 (Min/Max 23/37)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       139
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       586
194 Temperature_Celsius     0x0022   037   045   000    Old_age   Always       -       37 (0 22 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       171888886163360
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       19442243448753
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       73995335576865


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      1104         -


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


smartctl 5.41 2011-06-09 r3365 [i686-linux-3.0.0-30-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)


=== START OF INFORMATION SECTION ===
Device Model:     ST3000DM001-9YN166
Serial Number:    S1F0PVXL
LU WWN Device Id: 5 000c50 05172d3d4
Firmware Version: CC9F
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Fri Nov 15 18:06:22 2013 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(  575) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x3081)	SCT Status supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   114   099   006    Pre-fail  Always       -       68907400
  3 Spin_Up_Time            0x0003   094   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       252
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   075   060   030    Pre-fail  Always       -       38609156
  9 Power_On_Hours          0x0032   089   089   000    Old_age   Always       -       10160
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       252
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   064   057   045    Old_age   Always       -       36 (Min/Max 21/36)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       140
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       590
194 Temperature_Celsius     0x0022   036   043   000    Old_age   Always       -       36 (0 21 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       44942537795485
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       13220140376352
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       74197626284220


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      1104         -


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


smartctl 5.41 2011-06-09 r3365 [i686-linux-3.0.0-30-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)


=== START OF INFORMATION SECTION ===
Device Model:     ST3000DM001-9YN166
Serial Number:    S1F0NJB0
LU WWN Device Id: 5 000c50 05150aca1
Firmware Version: CC9F
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Fri Nov 15 18:06:32 2013 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(  575) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x3081)	SCT Status supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   112   099   006    Pre-fail  Always       -       48283768
  3 Spin_Up_Time            0x0003   094   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       252
  5 Reallocated_Sector_Ct   0x0033   088   051   036    Pre-fail  Always       -       16896
  7 Seek_Error_Rate         0x000f   075   060   030    Pre-fail  Always       -       37774618
  9 Power_On_Hours          0x0032   089   089   000    Old_age   Always       -       10161
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       252
183 Runtime_Bad_Block       0x0032   099   099   000    Old_age   Always       -       1
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   097   097   000    Old_age   Always       -       4295163907
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   063   057   045    Old_age   Always       -       37 (Min/Max 22/37)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       141
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       600
194 Temperature_Celsius     0x0022   037   043   000    Old_age   Always       -       37 (0 22 0 0)
197 Current_Pending_Sector  0x0012   045   045   000    Old_age   Always       -       9104
198 Offline_Uncorrectable   0x0010   045   045   000    Old_age   Offline      -       9104
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       219099166680990
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       8662826176396
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       72217958925623


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Aborted by host               10%     10149         -
# 2  Extended offline    Completed without error       00%      1104         -


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


smartctl 5.41 2011-06-09 r3365 [i686-linux-3.0.0-30-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)


=== START OF INFORMATION SECTION ===
Device Model:     ST3000DM001-9YN166
Serial Number:    S1F0PZKV
LU WWN Device Id: 5 000c50 05171bf71
Firmware Version: CC9F
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Fri Nov 15 18:06:43 2013 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(  584) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x3081)	SCT Status supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   099   006    Pre-fail  Always       -       166673224
  3 Spin_Up_Time            0x0003   094   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       268
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   064   060   030    Pre-fail  Always       -       51580933965
  9 Power_On_Hours          0x0032   089   089   000    Old_age   Always       -       10160
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       267
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   099   000    Old_age   Always       -       1
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   064   052   045    Old_age   Always       -       36 (Min/Max 22/36)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       155
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       597
194 Temperature_Celsius     0x0022   036   048   000    Old_age   Always       -       36 (0 22 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       268839182935970
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       9320372934352
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       66420802565831


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      1105         -
# 2  Short offline       Completed without error       00%         0         -


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


smartctl 5.41 2011-06-09 r3365 [i686-linux-3.0.0-30-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)


=== START OF INFORMATION SECTION ===
Device Model:     ST3000DM001-1CH166
Serial Number:    Z1F3WH08
LU WWN Device Id: 5 000c50 065024af6
Firmware Version: CC26
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Fri Nov 15 18:06:53 2013 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(   97) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x3085)	SCT Status supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   006    Pre-fail  Always       -       704168
  3 Spin_Up_Time            0x0003   096   096   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       6
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   253   030    Pre-fail  Always       -       9259
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       10
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       6
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   064   061   045    Old_age   Always       -       36 (Min/Max 20/36)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       4
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       19
194 Temperature_Celsius     0x0022   036   040   000    Old_age   Always       -       36 (0 20 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       264496970989573
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       937808
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       103796


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]




SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


thanks

---

### Post by SaturnusDJ on 2013-11-16
Please next time put outputs in code blocks.

```
LU WWN Device Id: 5 000c50 05150aca1
```
That one probably is dead. Very high Reallocated Sector and Current Pending Sector counts.

The best try here is to recover this drive to a new disk with a tool like mentioned here: [http://askubuntu.com/questions/211578/whats-the-difference-between-ddrescue-gddrescue-and-dd-rescue](http://askubuntu.com/questions/211578/whats-the-difference-between-ddrescue-gddrescue-and-dd-rescue)


What output do you get when you try to assemble?


Also something is up with /dev/sda. It's the only disk having a "Recovery Offset." I'll read into that and get back later.

---

### Post by mshogg on 2013-11-16
Hi, what assemble should i try? just assemble by itself or with scan or force please?

---

### Post by mshogg on 2013-11-16
hmm

just ran a mdadm --detail /dev/md0 and got this.  sda rebuilding? maybe why it was a strange error before, also no 5 is removed? this is the new drive, sdf i assume?

/dev/md0:
        Version : 1.2
  Creation Time : Tue Oct 23 12:12:32 2012
     Raid Level : raid5
  Used Dev Size : -1
   Raid Devices : 6
  Total Devices : 5
    Persistence : Superblock is persistent


    Update Time : Mon Nov 11 22:16:01 2013
          State : active, FAILED, Not Started
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1


         Layout : left-symmetric
     Chunk Size : 64K


           Name : proliant:0  (local to host proliant)
           UUID : cb39f990:2e3f054c:73624174:a29f8aae
         Events : 126796


    Number   Major   Minor   RaidDevice State
       0       8        0        0      spare rebuilding   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       8       48        3      active sync   /dev/sdd
       4       8       64        4      active sync   /dev/sde
       5       0        0        5      removed

---

### Post by mshogg on 2013-11-16
ran a cat /proc/mdstat and it doesnt show the 6th disk and says inactive whereas the above said active?

Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md0 : inactive sda[0] sdd[3] sde[4] sdb[1] sdc[2]
      14651327800 blocks super 1.2
       
unused devices: <none>

---

### Post by mshogg on 2013-11-16
ran a mdadm --examine /dev/d=sd[abcde..] and got the following:- looks like the last disk is missing, its the one i removed and replaced with new drive, but i only removed it physically i didnt run any commands to remove, could this be the problem? I have all of my data on here, i cannot afford to lose it :o( i can paypal someone $50 if you can get me up and running again please?

/dev/sda:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x3
     Array UUID : cb39f990:2e3f054c:73624174:a29f8aae
           Name : proliant:0  (local to host proliant)
  Creation Time : Tue Oct 23 12:12:32 2012
     Raid Level : raid5
   Raid Devices : 6


 Avail Dev Size : 5860531120 (2794.52 GiB 3000.59 GB)
     Array Size : 29302654080 (13972.59 GiB 15002.96 GB)
  Used Dev Size : 5860530816 (2794.52 GiB 3000.59 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
Recovery Offset : 23766016 sectors
          State : clean
    Device UUID : 060426e7:0142a39a:72c8be59:cc246c3a


Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Nov 11 22:16:01 2013
       Checksum : fe234fd2 - correct
         Events : 126796


         Layout : left-symmetric
     Chunk Size : 64K


   Device Role : Active device 0
   Array State : AAAAA. ('A' == active, '.' == missing)
/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : cb39f990:2e3f054c:73624174:a29f8aae
           Name : proliant:0  (local to host proliant)
  Creation Time : Tue Oct 23 12:12:32 2012
     Raid Level : raid5
   Raid Devices : 6


 Avail Dev Size : 5860531120 (2794.52 GiB 3000.59 GB)
     Array Size : 29302654080 (13972.59 GiB 15002.96 GB)
  Used Dev Size : 5860530816 (2794.52 GiB 3000.59 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 0c7e3646:65476908:64245949:1b39050b


Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Nov 11 22:16:01 2013
       Checksum : 89c29b7b - correct
         Events : 126796


         Layout : left-symmetric
     Chunk Size : 64K


   Device Role : Active device 1
   Array State : AAAAA. ('A' == active, '.' == missing)
/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : cb39f990:2e3f054c:73624174:a29f8aae
           Name : proliant:0  (local to host proliant)
  Creation Time : Tue Oct 23 12:12:32 2012
     Raid Level : raid5
   Raid Devices : 6


 Avail Dev Size : 5860531120 (2794.52 GiB 3000.59 GB)
     Array Size : 29302654080 (13972.59 GiB 15002.96 GB)
  Used Dev Size : 5860530816 (2794.52 GiB 3000.59 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : a4256fb7:a4a571f3:0cf5af02:633246ba


Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Nov 11 22:16:01 2013
       Checksum : 4e9b6b45 - correct
         Events : 126796


         Layout : left-symmetric
     Chunk Size : 64K


   Device Role : Active device 2
   Array State : AAAAA. ('A' == active, '.' == missing)
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : cb39f990:2e3f054c:73624174:a29f8aae
           Name : proliant:0  (local to host proliant)
  Creation Time : Tue Oct 23 12:12:32 2012
     Raid Level : raid5
   Raid Devices : 6


 Avail Dev Size : 5860531120 (2794.52 GiB 3000.59 GB)
     Array Size : 29302654080 (13972.59 GiB 15002.96 GB)
  Used Dev Size : 5860530816 (2794.52 GiB 3000.59 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 0609fe4a:1d57d31f:e5618980:18881091


Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Nov 11 22:16:01 2013
       Checksum : 632fc2ae - correct
         Events : 126796


         Layout : left-symmetric
     Chunk Size : 64K


   Device Role : Active device 3
   Array State : AAAAA. ('A' == active, '.' == missing)
/dev/sde:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : cb39f990:2e3f054c:73624174:a29f8aae
           Name : proliant:0  (local to host proliant)
  Creation Time : Tue Oct 23 12:12:32 2012
     Raid Level : raid5
   Raid Devices : 6


 Avail Dev Size : 5860531120 (2794.52 GiB 3000.59 GB)
     Array Size : 29302654080 (13972.59 GiB 15002.96 GB)
  Used Dev Size : 5860530816 (2794.52 GiB 3000.59 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : fb9f2b5c:356c1ef3:14a27d62:8288b98d


Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Nov 11 22:16:01 2013
       Checksum : 2645af56 - correct
         Events : 126796


         Layout : left-symmetric
     Chunk Size : 64K


   Device Role : Active device 4
   Array State : AAAAA. ('A' == active, '.' == missing)

---

### Post by SaturnusDJ on 2013-11-16
Try a normal assemble, without force/run.
```
mdadm --assemble /dev/md0 --uuid=cb39f990:2e3f054c:73624174:a29f8aae

```

Look at 
```

cat /proc/mdstat

```
to see what happens.

Again: please outputs in [code] brackets.

---

### Post by mshogg on 2013-11-16
Hi SaturnusDJ

i dont know how to output in code or even what that means, at minute i am outputting to a txt file then pasting in here, can you tell me how please?

anyway, ran the assemble command as you requested and it went onto the next line no error etc, then ran a cat /proc/mdstat and got this, not seeing my 6th new drive and cant see any % rebuild listed?

Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md0 : inactive sda[0] sdd[3] sde[4] sdb[1] sdc[2]
      14651327800 blocks super 1.2
       
unused devices: <none>

---

### Post by SaturnusDJ on 2013-11-16
Here on the forum where you post outputs of commands, you post like this:
[ code ]
Then put output in the middle.
[ /code ]
But without the spaces inside the brackets.

At this moment I don't know what's up with "Recovery Offset." It probably means recovery was in progress but stopped somewhere. Might be because of that one drive with much S.M.A.R.T. error failing. That one needs to be rescued to a new disk.
Cancelling or ignoring the recovery might be the end of your data. Let's hope a more expert sees this topic too.

---

### Post by mshogg on 2013-11-16
Ok well thanks for your time and help SaturnusDJ, much appreciated

---

### Post by mshogg on 2013-11-21
hi guys

is there anyone out there that can help please?

---

