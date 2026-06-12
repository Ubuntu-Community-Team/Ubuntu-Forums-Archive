---
title: "mdadm array inactive after reboot"
date: 2017-06-28
forum: General Help
---

### Post by jzambon on 2017-06-28
I've been having some issues with a RAID array (RAID5 with 3 drives, 2 + 1 redundant) on my system recently.  I backed up everything and replaced 2 older hard drives that appeared to be failing (didn't save the smartctl logs).  I built the new array last night and it appeared to be working well.  I followed these instructions under the RAID5 heading.  [https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04)

```

cat /proc/mdstat   [sees inactive array in /dev/md127]
sudo mdadm --stop /dev/md127
sudo mdadm --remove /dev/md127
cat /proc/mdstat   [lost inactive array in /dev/md127]
lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT   [verifies disks to be used]
sudo mdadm --zero-superblock /dev/sda
sudo mdadm --zero-superblock /dev/sdc
sudo mdadm --zero-superblock /dev/sdd
sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda /dev/sdc /dev/sdd
cat /proc/mdstat   [checks status of array build, impatience -> x1000 times]
[array build done and successful]
sudo mkfs.ext4 -F /dev/md0  [successful partitioning of new array on /dev/md0]
sudo mkdir /raid/
sudo mount /dev/md0 /raid/  [succssful mounting of new array on /raid/]
df -h   [array visible and with appropriate size]
cat /proc/mdstat   [active RAID5 array 2+1]
sudo mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf   [array configuration saved]
sudo update-initramfs -u   ["Afterwards, you can update the initramfs, or initial RAM file system, so that the array will be available during the early boot process"]
echo '/dev/md0 /mnt/md0 ext4 defaults,nofail,discard 0 0' | sudo tee -a /etc/fstab   [filesystem added to fstab]
sudo vi /etc/fstab   [verified its in there]
sudo shutdown -r now   [restart, cross fingers]



```

Upon restart, the system hung at waiting for /raid/.  I told it to skip, logged in and noticed that the array went inactive once again.  Frustrated, I stopped the raid and tried to reassemble after verifying with dmesg that the appropriate drives were there...

```

sudo mdadm --stop /dev/md0
**sudo mdadm --assemble --force /dev/md0 /dev/sda /dev/sdc /dev/sdd**
**mdadm: no RAID superblock on /dev/sdd**
**mdadm: /dev/sdd has no superblock - assembly aborted**

```

After replacing /dev/sda and /dev/sdb, /dev/sdd is now the oldest drive in the array (1.5yrs old), so I assumed that it might be having problems.  I found some advice [here]("https://ubuntuforums.org/showthread.php?t=1947275") suggesting I check smartctl and run a long SMART test on it...

```

sudo smartctl -t long /dev/sdd
sudo smartctl -d ata -a /dev/sdd
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-4.2.0-30-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Red (AF)
Device Model:     WDC WD30EFRX-68EUZN0
Serial Number:    WD-WCC4N4SSDC4L
LU WWN Device Id: 5 0014ee 261e584cb
Firmware Version: 82.00A82
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Wed Jun 28 10:08:59 2017 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 247)    Self-test routine in progress...
                    70% of test remaining.
Total time to complete Offline 
data collection:         (39240) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 394) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x703d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   183   177   021    Pre-fail  Always       -       5833
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       51
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   084   084   000    Old_age   Always       -       12248
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       51
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       33
193 Load_Cycle_Count        0x0032   196   196   000    Old_age   Always       -       12107
194 Temperature_Celsius     0x0022   119   114   000    Old_age   Always       -       31
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Aborted by host               90%     12246         -    <- Ignore this, I got impatient and cancelled the first test to restart


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

SMART test has been going for about 90 minutes now (30% complete).  I'm just wondering if there is anything else I should be looking at.  Additional dumb question... should I be concerned about other (non-HDD) hardware issues?  I've fallen victim in the past thinking that a faulty SSD was to blame when in fact it was an old motherboard or power supply.  My current ones are about 18 months old and have shown no issues.

Thanks!

---

### Post by jzambon on 2017-06-29
Fixed.

I'm stupid and didn't partition the individual drives before making the RAID.  After restarting they couldn't find the partitions because they did not exist because I'm stupid.  The instructions didn't have the partitioning clear and I am stupid.

```

sudo mdadm --zero-superblock /dev/sda
sudo mdadm --zero-superblock /dev/sdc
sudo mdadm --zero-superblock /dev/sdd
sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda /dev/sdc /dev/sdd

```

tl;dr I'm stupid.

---

