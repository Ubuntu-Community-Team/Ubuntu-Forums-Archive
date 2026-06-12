---
title: "3TB external hard drive lost capacity, only shows 1TB."
date: 2016-06-16
forum: General Help
---

### Post by J_Me on 2016-06-16
My computer crashed(kernel panic) while copying a file to a external hard drive and have now lost over half of the capacity of the external drive including a lot of files.
In brief when I right click properties for the drive it only shows 1.1TB of total disk space but it should be 3TB. It's like a platter inside the drive is not mounting or has just disappeared.
I ran a smartctl test on the external drive a week before the crash and another afterwards (please note I had to remove the drive from it's enclosure in order to run the smart test). I tried searching for any hidden files but only one .directory file showed up. Also tried fsck and e2fsck but didn't fix it. Any help is appreciated, results below.

```
This is some of the message from the kernel panic crash.

kernel BUG at /build/linux-ltd-utopic-NPr3jD/linux-lts-utopic-3.16.0/block/blk-core.c:12781


Invslid opcode: 0000 [#1] SMP


CPU: 5 PID: 0 Comm: swapper/5 Tainted: P    OE 3.16.0-71-generic #92''14.04.1-Ubuntu


kernel panic - not syncing: Fatal exception in interupt


Shutting down cpus with NNI


drm_kms_helper: panic occurred, switching back to text console
```

```
This test ran on 02 june 16 before the crash

$ sudo smartctl -a /dev/sdc
                                                                                                                                                                                        
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.16.0-71-generic] (local build)                                                                                                                                       
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org                                                                                                                                        
                                                                                                                                                                                                                   
=== START OF INFORMATION SECTION ===                                                                                                                                                                               
Model Family:     Seagate Barracuda 7200.14 (AF)                                                                                                                                                                   
Device Model:     ST3000DM001-1E6166                                                                                                                                                                               
Serial Number:    Z1F3DV73                                                                                                                                                                                         
LU WWN Device Id: 5 000c50 06413f52e                                                                                                                                                                               
Firmware Version: SC47                                                                                                                                                                                             
User Capacity:    3,000,592,982,016 bytes [3.00 TB]                                                                                                                                                                
Sector Sizes:     512 bytes logical, 4096 bytes physical                                                                                                                                                           
Rotation Rate:    7200 rpm                                                                                                                                                                                         
Device is:        In smartctl database [for details use: -P show]                                                                                                                                                  
ATA Version is:   ATA8-ACS T13/1699-D revision 4                                                                                                                                                                   
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 1.5 Gb/s)                                                                                                                                                           
Local Time is:    Thu Jun  2 12:23:29 2016 BST                                                                                                                                                                     
                                                                                                                                                                                                                   
==> WARNING: A firmware update for this drive may be available,                                                                                                                                                    
see the following Seagate web pages:                                                                                                                                                                               
http://knowledge.seagate.com/articles/en_US/FAQ/207931en                                                                                                                                                           
http://knowledge.seagate.com/articles/en_US/FAQ/223651en                                                                                                                                                           
                                                                                                                                                                                                                   
SMART support is: Available - device has SMART capability.                                                                                                                                                         
SMART support is: Enabled                                                                                                                                                                                          
                                                                                                                                                                                                                   
=== START OF READ SMART DATA SECTION ===                                                                                                                                                                           
SMART overall-health self-assessment test result: PASSED                                                                                                                                                           
See vendor-specific Attribute list for marginal Attributes.                                                                                                                                                        


General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (  584) seconds.
Offline data collection
capabilities:                    (0x73) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        No Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 373) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x3081) SCT Status supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   114   099   006    Pre-fail  Always       -       70953320
  3 Spin_Up_Time            0x0003   092   091   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1052
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   054   051   030    Pre-fail  Always       -       150333445787
  9 Power_On_Hours          0x0032   089   089   000    Old_age   Always       -       9713
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1047
183 Runtime_Bad_Block       0x0032   099   099   000    Old_age   Always       -       1
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0 0 0
189 High_Fly_Writes         0x003a   096   096   000    Old_age   Always       -       4
190 Airflow_Temperature_Cel 0x0022   066   038   045    Old_age   Always   In_the_past 34 (22 3 34 34 0)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       1032
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       10090
194 Temperature_Celsius     0x0022   034   062   000    Old_age   Always       -       34 (0 19 0 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       5632h+29m+33.661s
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       7073734290
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       36556253381


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
```

```
Test run on 14 june 16 after the crash

$ sudo smartctl -a /dev/sdc


smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.16.0-73-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.14 (AF)
Device Model:     ST3000DM001-1E6166
Serial Number:    Z1F3DV73                                                                                                                                                                    
LU WWN Device Id: 5 000c50 06413f52e                                                                                                                                                          
Firmware Version: SC47                                                                                                                                                                        
User Capacity:    3,000,592,982,016 bytes [3.00 TB]                                                                                                                                           
Sector Sizes:     512 bytes logical, 4096 bytes physical                                                                                                                                      
Rotation Rate:    7200 rpm                                                                                                                                                                    
Device is:        In smartctl database [for details use: -P show]                                                                                                                             
ATA Version is:   ATA8-ACS T13/1699-D revision 4                                                                                                                                              
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 1.5 Gb/s)                                                                                                                                      
Local Time is:    Tue Jun 14 11:02:29 2016 BST                                                                                                                                                
                                                                                                                                                                                              
==> WARNING: A firmware update for this drive may be available,                                                                                                                               
see the following Seagate web pages:                                                                                                                                                          
http://knowledge.seagate.com/articles/en_US/FAQ/207931en                                                                                                                                      
http://knowledge.seagate.com/articles/en_US/FAQ/223651en                                                                                                                                      
                                                                                                                                                                                              
SMART support is: Available - device has SMART capability.                                                                                                                                    
SMART support is: Enabled                                                                                                                                                                     
                                                                                                                                                                                              
=== START OF READ SMART DATA SECTION ===                                                                                                                                                      
SMART overall-health self-assessment test result: PASSED                                                                                                                                      
See vendor-specific Attribute list for marginal Attributes.                                                                                                                                   
                                                                                                                                                                                              
General SMART Values:                                                                                                                                                                         
Offline data collection status:  (0x00) Offline data collection activity                                                                                                                      
                                        was never started.                                                                                                                                    
                                        Auto Offline Data Collection: Disabled.                                                                                                               
Self-test execution status:      (   0) The previous self-test routine completed                                                                                                              
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (  584) seconds.
Offline data collection
capabilities:                    (0x73) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        No Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 373) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x3081) SCT Status supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   119   099   006    Pre-fail  Always       -       222178352
  3 Spin_Up_Time            0x0003   092   091   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1088
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   054   051   030    Pre-fail  Always       -       154628452976
  9 Power_On_Hours          0x0032   089   089   000    Old_age   Always       -       9757
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1083
183 Runtime_Bad_Block       0x0032   099   099   000    Old_age   Always       -       1
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       12 12 12
189 High_Fly_Writes         0x003a   096   096   000    Old_age   Always       -       4
190 Airflow_Temperature_Cel 0x0022   064   038   045    Old_age   Always   In_the_past 36 (22 74 36 35 0)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       1068
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       10169
194 Temperature_Celsius     0x0022   036   062   000    Old_age   Always       -       36 (0 19 0 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       8
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       8
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       5660h+49m+55.647s
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       7073738986
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       36700766509


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      9713         -


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
```

```
Also had a go with fsck.



$ sudo fsck /dev/sdc
fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdc


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>




$ sudo e2fsck -b 32768 /dev/sdc
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: Bad magic number in super-block while trying to open /dev/sdc


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
```

```
Ran fdisk on the drive with and without enclosure attached.



WITH EXTERNAL ENCLOSURE
$ sudo fdisk /dev/sdc


Note: sector size is 4096 (not 512)


Command (m for help): p


Disk /dev/sdc: 3000.6 GB, 3000592977920 bytes
255 heads, 63 sectors/track, 45600 cylinders, total 732566645 sectors
Units = sectors of 1 * 4096 = 4096 bytes                                                                                                                                                      
Sector size (logical/physical): 4096 bytes / 4096 bytes                                                                                                                                       
I/O size (minimum/optimal): 4096 bytes / 268431360 bytes                                                                                                                                      
Disk identifier: 0x90a69cfd                                                                                                                                                                   
                                                                                                                                                                                              
   Device Boot      Start         End      Blocks   Id  System                                                                                                                                
/dev/sdc1            2048   732566641  2930258376   83  Linux                                                                                                                                 
                                                                                                                                                                                              
Command (m for help):   






WITHOUT EXTERNAL ENCLOSURE
$ sudo fdisk /dev/sdc




WARNING: The size of this disk is 3.0 TB (3000592982016 bytes).
DOS partition table format can not be used on drives for volumes
larger than (2199023255040 bytes) for 512-byte sectors. Use parted(1) and GUID 
partition table format (GPT).




Command (m for help): p


Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x90a69cfd


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   732566641   366282297   83  Linux


Command (m for help): 
```

---

### Post by oldfred on 2016-06-16
Did you list actual backup superblocks and try several?
 List backup superblocks:
sudo dumpe2fs /dev/sdc1 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sdc1
One user could not get partition unmounted (may have needed swapoff), but used another live distro 


 List backup superblocks:
sudo dumpe2fs /dev/sdc1 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sdc1
One user could not get partition unmounted (may have needed swapoff), but used another live distro 

      
 [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)


 Last ditch redo superblocks, best to only do if you have good backup:
[http://ubuntuforums.org/showthread.php?t=1681972&page=5](http://ubuntuforums.org/showthread.php?t=1681972&page=5)
Worked for this user:
[http://ubuntuforums.org/showthread.php?t=2033778](http://ubuntuforums.org/showthread.php?t=2033778)
[http://ubuntuforums.org/showthread.php?t=1684746](http://ubuntuforums.org/showthread.php?t=1684746)
Some additional advanced ways:
[http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/](http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/)
[http://www.hanksaves.com/hddrecovery/index.php/Welcome_to_Hank%27s_Data_Recovery_Wiki](http://www.hanksaves.com/hddrecovery/index.php/Welcome_to_Hank%27s_Data_Recovery_Wiki)

---

### Post by J_Me on 2016-06-16
Thanks for the reply,
Just a quick question before I start, should I be working on this drive in or out of the enclosure as I seem to be getting different results from running the same tests.

I'm getting an Error 404 - Page not found for this page, do you have another link [http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)

But to answer your question, no I didn't list backup superblocks, I only used fsck and e2fsck for the first time on this drive ('sudo fsck /dev/sdc' 'sudo e2fsck -b 32768 /dev/sdc').

I'll read the links you posted and will get back to you later.
And thanks again for your help

---

### Post by Habitual on 2016-06-16
^ 404 here also.

---

### Post by J_Me on 2016-06-17
Update,
@[COLOR=#000000]oldfred Thanks [/COLOR]I was able to get all my files back :)

@[COLOR=#000000]Habitual [/COLOR]This link works
[http://www.admon.org/system-tuning/using-alternative-superblock-to-check-ext3/](http://www.admon.org/system-tuning/using-alternative-superblock-to-check-ext3/)

And for anyone interested I didn't need to take the drive out of it's enclosure, I think this only applies to running smartctl on some usb3 dirves.

---

