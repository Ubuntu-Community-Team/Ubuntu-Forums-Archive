---
title: "Hard drive dying??"
date: 2008-02-08
forum: General Help
---

### Post by themusicwave on 2008-02-08
Hey everyone,

I just ran  sudo smartctl -a /dev/sda5 which is a partition on my laptop hard disk.

I get the following output> 
193 Load_Cycle_Count        0x0012   093   093   000    Old_age   Always       -       78465
jon@jon-laptop-ubuntu:/etc$ sudo smartctl
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

ERROR: smartctl requires a device name as the final command-line argument.


Use smartctl -h to get a usage summary

jon@jon-laptop-ubuntu:/etc$ sudo smartctl -a /dev/sda5
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     Hitachi HTS721010G9SA00
Serial Number:    MPCZN2Y0GR5RKH
Firmware Version: MCZOC10H
User Capacity:    98,522,403,840 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 1
Local Time is:    Fri Feb  8 19:24:16 2008 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 ( 645) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  50) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0004   115   115   000    Old_age   Offline      -       3421
  3 Spin_Up_Time            0x0007   223   223   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       1546
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000a   100   100   000    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0004   114   114   000    Old_age   Offline      -       39
  9 Power_On_Hours          0x0012   095   095   000    Old_age   Always       -       2190
 10 Spin_Retry_Count        0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1492
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   099   099   000    Old_age   Always       -       221
193 Load_Cycle_Count        0x0012   093   093   000    Old_age   Always       -       78465
194 Temperature_Celsius     0x0002   110   110   000    Old_age   Always       -       50 (Lifetime Min/Max 14/65)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       550         -
# 2  Short offline       Completed without error       00%       550         -
# 3  Short offline       Completed without error       00%         0         -

Warning! SMART Selective Self-Test Log Structure error: invalid SMART checksum.
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



I am a bit concerned abou tall those Old_age and Pre_fail listing....my laptop is only about 1.5 years old.

I do run regular backups to my external due to paranoia(and losing data in the past) an I also have a warranty for 2 more years.

could someone help me understand this data and what it means?

Thanks,

Jon

---

### Post by hamstersquasher on 2008-02-08
I would try to go to the harddrive manufacturer's website and download their harddrive diagnostics.  Often times you will have an option of downloading an .EXE for creating a floppy (which may work under linux IF you have wine installed) or download an .ISO file to burn to a cd.  Those downloadable diagnostics will have the final say on the state of your harddrive regardless of what any OS tells you.

---

### Post by nemarasu on 2008-02-08
I'm not sure how useful this output will be to you, as part of the output says:

Device is: Not in smartctl database [for details use: -P showall]

---

### Post by Herman on 2008-02-09
That looks okay to me, you don't even have any errors logged yet.

Look in your hard drive manufacturer's website for a list of attributes for your particular model of hard disk to compare your smartmontools outputs with if you can find one. 
[Support | Travelstar 7K100 datasheet]("http://www.hitachigst.com/hdd/support/7k100/7k100.htm")

[Travelstar 7K100 technical library]("http://www.hitachigst.com/tech/techlib.nsf/products/Travelstar_7K100") - ( try the datasheets and the specifictaions .pdf downloads).

An attribute is basically anything that the hard drive manufacturer think it's worth keeping an eye on and that might be a useful indicator of the health of the hard drive.
The numbers raw values are converted by whatever formula the manufacturer decided on to come up with the a VALUE. 
This VALUE is like a score out of 100 or a score out of 253 or whatever number they chose and represents the hard disk's present condition. 
You can compare that with the number in the WORST column, that's the worst value your hard disk has recorded for that attribute.
You can compare both the present VALUE and the WORST ever value with the number in the THRESH column, if your VALUE gets down as low as the number set as the THRESH (threshold), then a failure will be recorded.
Not all failures necessarily indicate your hard drive is 'kaput' because some failures are only temporary.

[Self-Monitoring, Analysis, and Reporting Technology]("http://en.wikipedia.org/wiki/Self-Monitoring,_Analysis,_and_Reporting_Technology")

[Self-Monitoring Analysis and Reporting Technology (SMART)]("http://www.storagereview.com/guide/featuresSMART.html")

Regards, Herman  :)

---

