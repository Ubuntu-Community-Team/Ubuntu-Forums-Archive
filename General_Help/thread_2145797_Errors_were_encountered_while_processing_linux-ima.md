---
title: "Errors were encountered while processing linux-image (Ubuntu13.04)"
date: 2013-05-16
forum: General Help
---

### Post by EddyTheB on 2013-05-16
I am unable to install new software, or upgrade. When I open Software Centre I get the message "New software can't be installed, because there is a problem with the software currently installed. Do you want to repair this problem now?" (clicking repair fails). If I do apt-get upgrade or similar I get more informative errors that suggest I do apt-get -f install, which results in this output:

$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-3.8.0-21-generic
Suggested packages:
  fdutils linux-doc-3.8.0 linux-source-3.8.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.8.0-21-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/12.4 MB of archives.
After this operation, 33.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 206224 files and directories currently installed.)
Unpacking linux-image-3.8.0-21-generic (from .../linux-image-3.8.0-21-generic_3.8.0-21.32_amd64.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.8.0-21-generic_3.8.0-21.32_amd64.deb (--unpack):
 unable to create `/boot/vmlinuz-3.8.0-21-generic.dpkg-new' (while processing `./boot/vmlinuz-3.8.0-21-generic'): Input/output error
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-21-generic /boot/vmlinuz-3.8.0-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-21-generic /boot/vmlinuz-3.8.0-21-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.8.0-21-generic_3.8.0-21.32_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Could anyone suggest how to fix a broken pipe? My internet remained conected (and working) throughout. Thank you in advance.

---

### Post by EddyTheB on 2013-05-16
An update, I hope some of this information might ring a bell somewhere:

A colleague thinks that the most worrying part of the error message is the "Input/output error". He suggests this might be bode ill for the hard disk. I've run a SMART self-test and it turned up no issues. In the process of fixing another issue though I have discovered that my /boot directory won't open. 

$ls /boot
ls: reading directory /boot: Input/output error

I think the other issue (it wouldn't boot straight to ubuntu, only to the black screen with the list) began 2 days ago when I tried and failed to configure flashcache to boot from and cache to the ssd for faster performance. I think the most likely explanation is that I screwed something up then, and hopefully not that my hard drive is preparing to fail. Does this seem plausible to anyone? Could anyone suggest a diagnosis test I could run?

---

### Post by matt_symes on 2013-05-16
Hi

What do your log files say ? Do they have any errors in them ?

How are your partitions laid out ? Is /boot on its own partition ?

Have you ran fsck on the partition ? 

```
sudo touch /forcefsck
```

The system must be able to read the /boot directory or it will not be able to boot up.

What does this return if you type it in the terminal ?

```
echo /boot/*
```

Does it return the contents of the directory ?

Did you run a long smart test on the hard drive ?

Kind regards

---

### Post by EddyTheB on 2013-05-16
Hi, thanks for responding, I hope I can answer your questions.

My partitions are as Ubuntu suggested when I installed, this is how they appear in System Monitor>File Systems:

```

[FONT=courier new]    device                                     directory     type     total
    /dev/mapper/ubuntu--vg-root   /                 ext4    975.9 GB
    /dev/sda1                                /boot           ext2   238.8 MB[/FONT]
```

If I go in to recovery mode and look at the system summary it says:
```

[FONT=courier new]    === Detailed disk usage ===
    Filesystem                               Size      Used   Avail   Use%  Mounted on
    /dev/mapper/ubuntu--vg-root   909G    82G     782G   10      /
    udev                                        3.8G       0      3.8G      0      /dev[/FONT]
```

So I think /boot has its own partition.

"echo /boot/*" returns "/boot/*", no list of directories (as I do get with "echo /etc/*").  

I ran a Short SMART self test. I'll run an extended one later.

I'm not really sure what I'm looking for in the log files, here are the first few entries from this morning 'CRITICAL' caught my eye...

```

[FONT=courier new]    May 16 08:04:11 Meadowlark anacron[1229]: Job `cron.daily' terminated (mailing output)
    May 16 08:04:11 Meadowlark anacron[1229]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
    May 16 08:04:11 Meadowlark anacron[1229]: Normal exit (1 job run) 
    May 16 08:04:20 Meadowlark AptDaemon.Worker: CRITICAL:  /var/cache/apt/archives/linux-image-3.8.0-21-generic_3.8.0-21.32_amd64.deb:  unable to create `/boot/vmlinuz-3.8.0-21-generic.dpkg-new' (while  processing `./boot/vmlinuz-3.8.0-21-generic'): Input/output error
[/FONT] [FONT=courier new]    May 16 08:05:05 Meadowlark AptDaemon.Worker: CRITICAL: linux-image-extra-3.8.0-21-generic: dependency problems - leaving unconfigured
    May 16 08:05:05 Meadowlark AptDaemon.Worker: CRITICAL: linux-image-generic: dependency problems - leaving unconfigured
    May 16 08:05:05 Meadowlark AptDaemon.Worker: CRITICAL: linux-generic: dependency problems - leaving unconfigured
    May 16 08:05:05 Meadowlark AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/ca775d3cbd9b4129975dc54b9dc83461[/FONT]
```

My system is booting up, so it must be reading boot at start up.

I ran fsck from recovery mode:

```

[FONT=courier new]    fsck from util-linux 2.20.1
    fsck from util-linux 2.20.1
    /dev/sda1: 263/124496 files (2.7% non-contiguous), 62254/248832 blocks
    /dev/mapper/ubuntu--vg-root: 517483/60530688 files (0.4% non-contiguous), 25082258/242095104 blocks

    Finished, please press ENTER[/FONT]
```

After I did that I did an "update grub bootloader". Then rebooted. After that I could access /boot so I thought it was fixed but then I did sudo apt-get update and sudo apt-get -f install, same problems as before, and again /boot can no longer be accessed. This doesn't happen after every start up, only after "update grub bootloader".

Other information, I thought I'd give mounting /boot a go (while it was not accessible):

```

[FONT=courier new]    $mount /boot
    mount: according to mtab, /dev/sdb is already mounted on /boot
    mount failed[/FONT]
```

Does any of that that make sense? Thanks again for your help.

---

### Post by matt_symes on 2013-05-16
Hi

So /boot is on its own seperate partition and you have raid and/or lvm.

/boot will be mounted onto the root partition and this is why you can't remount it, so that is not really an error.

Do you have a LiveCD/USB handy ?

You can run fsck in sda1 when it's not mounted. Boot into the LiveCD/USB

```
sudo e2fsck -f -y -v /dev/sda1
```

After you have run e2fsck, mount the partition sda1 in the liveCD/USB. Can you view the files then ?

```
sudo mount -t ext2 /dev/sda1 /mnt
```

```
ls /mnt
```

Boot into your system again.

To run a smart test

```
sudo apt-get install smartmontools
```

```
sudo smartctl -t long /dev/sda
```

This will take a while to complete but it should give you an extimated time.

When it has completed

```
sudo smartctl -a /dev/sda
```

You can post that back here.

To get more relevent info from the logs

```
grep -C5 "sda1" /var/log/syslog
```

What does this return ?

```
file -s /dev/sda1
```

```
ls -ld /boot
```

Kind regards

---

### Post by EddyTheB on 2013-05-17
Success!

I ran e2fsck from the live dvd, it all looked good, and mounting sda1 per your instructions worked and I was able to view the files.

I wasn't able to install smartctl, I got the usual error messages. But this time I ran "apt get -f install" and it worked. So I did upgrade too, and have installed smartctl and am running the test. I'll check the output when it's done but it seems like fsck fixed whatever was the problem.

Thank you so much for your help!

---

### Post by EddyTheB on 2013-05-21
Well, I can install now, but I think the underlying fault remains...

I tried to run update-grub to make my system boot straight to Ubuntu, and it failed with:

```

$ sudo update-grub
/usr/sbin/grub-mkconfig: 237: usr/sbin/mkconfig: cannot create /boot/grub/grub.cfg.new: Directory nonexistant
$ ls /boot
ls: reading directory /boot/: Input/output error

```

After that I thought to hell with it, and went to begin a reinstall, but got this informative error message popping up:
```

Two file systems are assigned the same mount point (/boot): SCSI1(0,0,0), partition #1 (sda) and SCSI2 (0,0,0) (sdb).

Please correct this by changing mount points.

```

So I thought that looked fixable, and had a look at this page for how to change mounting points ([https://help.ubuntu.com/community/MoveMountpointHowto](https://help.ubuntu.com/community/MoveMountpointHowto)). I didn't get much further than this:

```

$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000d17b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1953523711   976510977    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          501760  1953523711   976510976   8e  Linux LVM

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 8012 MB, 8012390400 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15649200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-root: 991.6 GB, 991621545984 bytes
255 heads, 63 sectors/track, 120557 cylinders, total 1936760832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 8275 MB, 8275361792 bytes
255 heads, 63 sectors/track, 1006 cylinders, total 16162816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

```
So it all looks like kind of a mess to me, compared to the nice output on the website.

My disk passed the smartcdl test (I can post output if that would help).


[FONT=arial]```
grep -C5 "sda1" /var/log/syslog
``` produces a lot of output, including lots of lines that say "```
sda: sda1 sda2 <sda5>[\CODE]", with "sda1" in red. 
Again, please let me know if it would still be useful to see the whole output.

Your other questions:
[CODE]
$ sudo file -s /dev/sda1
/dev/sda1: Linux rev 1.0 ext2 filesystem data, UUID=7761-etc-etc
$ ls -ld /boot
drwxr-xr-x 4 root root 1024 May 14 20:38 /boot

```  

Does any of that make sense? My instinct is still to reinstall, but perhaps the mounting and partition issues can be fixed without that?

Thank you again.
[/FONT]

---

### Post by matt_symes on 2013-05-21
Hi

> **EddyTheB said:**
> Well, I can install now, but I think the underlying fault remains...

I tried to run update-grub to make my system boot straight to Ubuntu, and it failed with:

```

$ sudo update-grub
/usr/sbin/grub-mkconfig: 237: usr/sbin/mkconfig: cannot create /boot/grub/grub.cfg.new: Directory nonexistant
$ ls /boot
ls: reading directory /boot/: Input/output error

```

After that I thought to hell with it, and went to begin a reinstall, but got this informative error message popping up:
```

Two file systems are assigned the same mount point (/boot): SCSI1(0,0,0), partition #1 (sda) and SCSI2 (0,0,0) (sdb).

Please correct this by changing mount points.

```

So I thought that looked fixable, and had a look at this page for how to change mounting points ([https://help.ubuntu.com/community/MoveMountpointHowto](https://help.ubuntu.com/community/MoveMountpointHowto)). I didn't get much further than this:

```

$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000d17b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1953523711   976510977    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          501760  1953523711   976510976   8e  Linux LVM

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 8012 MB, 8012390400 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15649200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-root: 991.6 GB, 991621545984 bytes
255 heads, 63 sectors/track, 120557 cylinders, total 1936760832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 8275 MB, 8275361792 bytes
255 heads, 63 sectors/track, 1006 cylinders, total 16162816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

```
So it all looks like kind of a mess to me, compared to the nice output on the website.

My disk passed the smartcdl test (I can post output if that would help).


[FONT=arial]```
grep -C5 "sda1" /var/log/syslog
``` produces a lot of output, including lots of lines that say "```
sda: sda1 sda2 <sda5>[\CODE]", with "sda1" in red. 
Again, please let me know if it would still be useful to see the whole output.

Your other questions:
[CODE]
$ sudo file -s /dev/sda1
/dev/sda1: Linux rev 1.0 ext2 filesystem data, UUID=7761-etc-etc
$ ls -ld /boot
drwxr-xr-x 4 root root 1024 May 14 20:38 /boot

```  

Does any of that make sense? My instinct is still to reinstall, but perhaps the mounting and partition issues can be fixed without that?

Thank you again.
[/FONT]

Did you get that error about 2 mount points from the LiveCD/USB when re-installing, on the partition page of the installer ? If so then you should be able to fix it from that screen, or the manual partition screen.

It would have been really helpful to see the full output of the SMART data and the syslog entries for SDA. Cross comparing them can reveal errors that SMART tests can miss.

Do you only have one disk inside the PC ? sdb (8G in size) has a GUID partition table and i assume this is a USB stick ?

Why are you using LVM if you have only one disk ? Did you expect to add more later ?

If the worse comes to the worse, i would use dd(rescue) to write zeros to the drive and then reinstall again, after that.

Kind regards

---

### Post by EddyTheB on 2013-05-21
I got that errror on the LiveCD when I clicked on the 'Reinstall Unbuntu' option.

I  don't have any particular plans to add more disks, but when I was  installing initially I saw the LVM option and did some quick research  and didn't find any reasons not to use it. I figured I may want to  partition my drive in future and it seemed to suggest this would be  easier with LVM.

The 8Gb sdb is an internal ssd that under the  initial windows 8 installation was used as a cache and to improve boot  times. I believe my problems are probably caused by an attempt to  install flashcache last week in the hope of reproducing that ability.

Thank you again for all your help.

Here's the SMART test output:
```

$ sudo smartctl -a /dev/sda
[sudo] password for eddy: 
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.8.0-21-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus SpinPoint M8 (AFT)
Device Model:     ST1000LM024 HN-M101MBB
Serial Number:    S2RQJ9AC807772
LU WWN Device Id: 5 0004cf 208398644
Firmware Version: 2AR10002
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 6
Local Time is:    Tue May 21 16:46:37 2013 MDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (13260) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 221) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0026   055   055   000    Old_age   Always       -       12320
  3 Spin_Up_Time            0x0023   089   089   025    Pre-fail  Always       -       3463
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       98
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       162
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       1
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       77
191 G-Sense_Error_Rate      0x0022   100   100   000    Old_age   Always       -       4
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   064   056   000    Old_age   Always       -       33 (Min/Max 19/44)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       8
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       1
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       1943

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       140         -
# 2  Extended offline    Interrupted (host reset)      90%        95         -
# 3  Extended offline    Aborted by host               90%        94         -
# 4  Extended offline    Interrupted (host reset)      80%        86         -
# 5  Short offline       Completed without error       00%        85         -
# 6  Short offline       Completed without error       00%         9         -
# 7  Short offline       Completed without error       00%         5         -

Note: selective self-test log revision number (0) not 1 implies that no selective self-test has ever been run
SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

And here is the log info:
```

$ grep -C5 "sda1" /var/log/syslog
May 21 07:41:59 Meadowlark kernel: [    1.812405] hub 1-1:1.0: 6 ports detected
May 21 07:41:59 Meadowlark kernel: [    1.815778] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
May 21 07:41:59 Meadowlark kernel: [    1.815782] cdrom: Uniform CD-ROM driver Revision: 3.20
May 21 07:41:59 Meadowlark kernel: [    1.815914] sr 2:0:0:0: Attached scsi CD-ROM sr0
May 21 07:41:59 Meadowlark kernel: [    1.815993] sr 2:0:0:0: Attached scsi generic sg2 type 5
May 21 07:41:59 Meadowlark kernel: [    1.842561]  sda: sda1 sda2 < sda5 >
May 21 07:41:59 Meadowlark kernel: [    1.842885] sd 0:0:0:0: [sda] Attached SCSI disk
May 21 07:41:59 Meadowlark kernel: [    1.923492] usb 2-1: new high-speed USB device number 2 using ehci-pci
May 21 07:41:59 Meadowlark kernel: [    2.055663] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
May 21 07:41:59 Meadowlark kernel: [    2.055666] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
May 21 07:41:59 Meadowlark kernel: [    2.055936] hub 2-1:1.0: USB hub found
--
May 21 12:18:52 Meadowlark kernel: [    1.804835] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SU-B08AB  SC01 PQ: 0 ANSI: 5
May 21 12:18:52 Meadowlark kernel: [    1.808048] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
May 21 12:18:52 Meadowlark kernel: [    1.808050] cdrom: Uniform CD-ROM driver Revision: 3.20
May 21 12:18:52 Meadowlark kernel: [    1.808152] sr 2:0:0:0: Attached scsi CD-ROM sr0
May 21 12:18:52 Meadowlark kernel: [    1.808212] sr 2:0:0:0: Attached scsi generic sg2 type 5
May 21 12:18:52 Meadowlark kernel: [    1.829641]  sda: sda1 sda2 < sda5 >
May 21 12:18:52 Meadowlark kernel: [    1.830152] sd 0:0:0:0: [sda] Attached SCSI disk
May 21 12:18:52 Meadowlark kernel: [    1.915443] usb 2-1: new high-speed USB device number 2 using ehci-pci
May 21 12:18:52 Meadowlark kernel: [    2.047627] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
May 21 12:18:52 Meadowlark kernel: [    2.047630] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
May 21 12:18:52 Meadowlark kernel: [    2.047765] hub 2-1:1.0: USB hub found
--
May 21 12:25:30 Meadowlark kernel: [    1.839448] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SU-B08AB  SC01 PQ: 0 ANSI: 5
May 21 12:25:30 Meadowlark kernel: [    1.843112] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
May 21 12:25:30 Meadowlark kernel: [    1.843114] cdrom: Uniform CD-ROM driver Revision: 3.20
May 21 12:25:30 Meadowlark kernel: [    1.843174] sr 2:0:0:0: Attached scsi CD-ROM sr0
May 21 12:25:30 Meadowlark kernel: [    1.843226] sr 2:0:0:0: Attached scsi generic sg2 type 5
May 21 12:25:30 Meadowlark kernel: [    1.867353]  sda: sda1 sda2 < sda5 >
May 21 12:25:30 Meadowlark kernel: [    1.867606] sd 0:0:0:0: [sda] Attached SCSI disk
May 21 12:25:30 Meadowlark kernel: [    1.943477] usb 2-1: new high-speed USB device number 2 using ehci-pci
May 21 12:25:30 Meadowlark kernel: [    2.075572] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
May 21 12:25:30 Meadowlark kernel: [    2.075575] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
May 21 12:25:30 Meadowlark kernel: [    2.075715] hub 2-1:1.0: USB hub found
--
May 21 12:40:40 Meadowlark kernel: [    1.808515] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SU-B08AB  SC01 PQ: 0 ANSI: 5
May 21 12:40:40 Meadowlark kernel: [    1.811877] sr0: scsi3-mmc drive: 24x/62x writer dvd-ram cd/rw xa/form2 cdda tray
May 21 12:40:40 Meadowlark kernel: [    1.811879] cdrom: Uniform CD-ROM driver Revision: 3.20
May 21 12:40:40 Meadowlark kernel: [    1.811970] sr 2:0:0:0: Attached scsi CD-ROM sr0
May 21 12:40:40 Meadowlark kernel: [    1.812048] sr 2:0:0:0: Attached scsi generic sg2 type 5
May 21 12:40:40 Meadowlark kernel: [    1.843450]  sda: sda1 sda2 < sda5 >
May 21 12:40:40 Meadowlark kernel: [    1.843805] sd 0:0:0:0: [sda] Attached SCSI disk
May 21 12:40:40 Meadowlark kernel: [    1.916211] usb 2-1: new high-speed USB device number 2 using ehci-pci
May 21 12:40:40 Meadowlark kernel: [    2.048422] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
May 21 12:40:40 Meadowlark kernel: [    2.048425] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
May 21 12:40:40 Meadowlark kernel: [    2.048558] hub 2-1:1.0: USB hub found

```

---

