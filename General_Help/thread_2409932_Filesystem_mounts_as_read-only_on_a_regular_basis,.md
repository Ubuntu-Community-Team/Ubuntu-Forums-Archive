---
title: "Filesystem mounts as read-only on a regular basis, fsck doesn't fix"
date: 2019-01-08
forum: General Help
---

### Post by Jugdish on 2019-01-08
I am having a recurring problem with my hard drive in which, roughly once a week, it will remount as read-only due to a read error. Every time this happens, I capture the output of dmesg, and it always reports the same sector number and inode number at fault.

dmesg:
```

[685549.546699] ata3.00: exception Emask 0x0 SAct 0x80000 SErr 0x0 action 0x0
[685549.546707] ata3.00: irq_stat 0x40000008
[685549.546714] ata3.00: failed command: READ FPDMA QUEUED
[685549.546725] ata3.00: cmd 60/08:98:28:3a:c1/00:00:0e:00:00/40 tag 19 ncq dma 4096 in
res 41/40:00:28:3a:c1/00:00:0e:00:00/40 Emask 0x409 (media error) <F>
[685549.546732] ata3.00: status: { DRDY ERR }
[685549.546736] ata3.00: error: { UNC }
[685549.548103] ata3.00: configured for UDMA/133
[685549.548127] sd 2:0:0:0: [sda] tag#19 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[685549.548132] sd 2:0:0:0: [sda] tag#19 Sense Key : Medium Error [current]
[685549.548137] sd 2:0:0:0: [sda] tag#19 Add. Sense: Unrecovered read error - auto reallocate failed
[685549.548142] sd 2:0:0:0: [sda] tag#19 CDB: Read(16) 88 00 00 00 00 00 0e c1 3a 28 00 00 00 08 00 00
[685549.548145] print_req_error: I/O error, dev sda, sector 247544360
[685549.548195] ata3: EH complete
[685549.548246] EXT4-fs error (device sda2): ext4_find_entry:1436: inode #7028795: comm updatedb.mlocat: reading directory lblock 0
[685549.591823] Aborting journal on device sda2-8.
[685549.616550] EXT4-fs (sda2): Remounting filesystem read-only

```

I have tried running ```
sudo fsck -c
``` on the filesystem after this happens, but it never detects inode #7028795 or sector 247544360 as being bad, so it doesn't get corrected.

What else can I do to mark this bad sector and stop it from continually remounting my filesystem as read-only?

I am running Ubuntu 16.04 and the filesystem type is ext4.

---

### Post by TheFu on 2019-01-08
Something is wrong, probably a hardware issue.  Could be anything in the chain - the SATA controller, the SATA cable, the disk controller or the physical disk.  Looks like the disk from the error.

a) make backups, constantly. Something is failing.  
b) get a replacement drive.  ATA/133 is really old. Amazing it has lasted this long.

I'd look at the SMART data to see the main 5 attributes which correlate directly to a nearly dead disk.  Relocated Sector count over 3 makes me pull a disk from use.```

Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   176   175   021    Pre-fail  Always       -       2191
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       167
_  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0_
_  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0_
  9 Power_On_Hours          0x0032   033   033   000    Old_age   Always       -       49591
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       163
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       120
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       46
194 Temperature_Celsius     0x0022   111   096   000    Old_age   Always       -       32
_196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0_
_197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0_
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
_199 UDMA_CRC_Error_Count    0x0032   200   001   000    Old_age   Always       -       370_
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0
```
are the main ones I watch.  The 199 attr was due to a bad SATA cable and has been corrected.  As you can see, this drive has been running over 5.5 yrs.

Mounting as read-only is the OSes way to protect your data and **do no more harm.**  It won't get better. I've seen SSD storage do this weekly for a few months before total failure, never to be readable again.

---

### Post by Jugdish on 2019-01-09
Thanks for your response. Just to clarify, the disk is SATA (not sure where you inferred ATA/133 from) and was purchased in Feb 2014.

Disk ident:
```

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Red
Device Model:     WDC WD40EFRX-68WT0N0
Serial Number:    WD-WCC4E0470092
LU WWN Device Id: 5 0014ee 209370065
Firmware Version: 80.00A80
User Capacity:    4,000,787,030,016 bytes [4.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Wed Jan  9 11:20:53 2019 PST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

```

The only reason I haven't immediately jumped on a new drive is because it's only reporting a single bad sector. If it was more than one it would be worried about drive failure.

That said, I have dumped the SMART attributes as suggested. On the surface it looks not great, but I'm unclear how to interpret this data. You mentioned the Reallocated Sector Count as a good indicator -- why is that, what does it mean?
Based on these values, how urgently would you say the drive needs to be replaced?
```

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       554
  3 Spin_Up_Time            0x0027   198   172   021    Pre-fail  Always       -       7083
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       80
  5 Reallocated_Sector_Ct   0x0033   196   196   140    Pre-fail  Always       -       122
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   043   043   000    Old_age   Always       -       41903
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       80
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       39
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       807784
194 Temperature_Celsius     0x0022   109   097   000    Old_age   Always       -       43
196 Reallocated_Event_Count 0x0032   188   188   000    Old_age   Always       -       12
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       174
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0

```

---

### Post by TheFu on 2019-01-09
You should replace that drive immediately. I wouldn't use it for anything going forward, not even sneakernet.
```

  5 Reallocated_Sector_Ct   0x0033   196   196   140    Pre-fail  Always       -       122
196 Reallocated_Event_Count 0x0032   188   188   000    Old_age   Always       -       12
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       174
```

You are out of reserved sectors and 174 failed sectors are gone, never to come back. Move. Now. Today. Immediately.  The drive is dying and you've already lost data.

Why did I think it was IDE?
```
[685549.548103] ata3.00: configured for UDMA/133
```

---

### Post by Jugdish on 2019-01-09
Yikes! Ok, new drive has been ordered!
Thanks for your help!

---

### Post by g.reys on 2019-01-10
Let us know how you get on with replacing the driver, but yes - it's a standard safety measure that OS would switch disk to read-only when filesystem reports unrecoverable errors: limit the amount of potential data loss (failed attempts to write/update something) AND get you to notice because many apps start complaining that they can't writing anything anymore.

---

### Post by TheFu on 2019-01-10
> **Jugdish said:**
> Yikes! Ok, new drive has been ordered!
Thanks for your help!

Please mark this thread as solved - "Thread tools" button near the top. That helps others.  Your SMART data is very clear and would help lots of people.  BTW, I underlined the data attributes that I watch, if that wasn't clear.  Also, I generally use the 'raw value' since the other _normalized_ values can mean anything. There isn't any industry standard.  The USgovt mandated that storage devices provide _some data_, but it wasn't specific, so every drive maker made stuff up.

You have 122 bad sectors already moved to spares.  No more spares exist and 174 additional sectors that would be relocated if they could are waiting.  You can look up what each of those attributes means online.

A WD-Red is a reasonably good drive BTW.  I have a few of them and haven't seen issues.  Also have a few HGST and Toshibas.  All fine drives based on Backblaze failure numbers.  I've had 2 HGST 4T drives fail, purchased 3 yrs apart.  Going forward, I'll probably buy WD-8TB drives when I don't get WD-Black or SSDs.  NVMe SSDs have a serious issue - no SMART data, which means we don't get any warning before failure.  If you don't pay attention to SMART, then it doesn't matter.  I watch SMART data weekly on all my disks, so I usually get some warning that a failure is coming.  However, SMART doesn't show anything bad 22% of the time that HDDs fail according to backblaze.

I hope you bought 2 replacement disks.  A primary and a backup.  You've already lost data. Hopefully, it is data you don't need because without a backup, it is gone.  I always get 2 disks at a time ... or storage is available to sufficiently backup the new storage.  For example, by moving some backup storage around, getting an 8tb disk let me get 2x4TB of primary storage available for the cost of a single 8TB hdd.  Backblaze stats show that pretty much any 8TB hdd bought will have less than 1% failure rates.  That's pretty good.

SMART is far from perfect, but it is all we have besides kernel errors in our logs.

---

### Post by CatKiller on 2019-01-10
> **TheFu said:**
>  NVMe SSDs have a serious issue - no SMART data

NVMe drives have plenty of SMART data.

```

sudo smartctl --all /dev/nvme0
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.18.0-13-lowlatency] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Number:                       Samsung SSD 970 EVO 1TB
Serial Number:                      S467NX0K710139Y
Firmware Version:                   1B2QEXE7
PCI Vendor/Subsystem ID:            0x144d
IEEE OUI Identifier:                0x002538
Total NVM Capacity:                 1,000,204,886,016 [1.00 TB]
Unallocated NVM Capacity:           0
Controller ID:                      4
Number of Namespaces:               1
Namespace 1 Size/Capacity:          1,000,204,886,016 [1.00 TB]
Namespace 1 Utilization:            388,168,953,856 [388 GB]
Namespace 1 Formatted LBA Size:     512
Local Time is:                      Thu Jan 10 15:41:03 2019 GMT
Firmware Updates (0x16):            3 Slots, no Reset required
Optional Admin Commands (0x0017):   Security Format Frmw_DL *Other*
Optional NVM Commands (0x005f):     Comp Wr_Unc DS_Mngmt Wr_Zero Sav/Sel_Feat *Other*
Maximum Data Transfer Size:         512 Pages
Warning  Comp. Temp. Threshold:     85 Celsius
Critical Comp. Temp. Threshold:     85 Celsius

Supported Power States
St Op     Max   Active     Idle   RL RT WL WT  Ent_Lat  Ex_Lat
 0 +     6.20W       -        -    0  0  0  0        0       0
 1 +     4.30W       -        -    1  1  1  1        0       0
 2 +     2.10W       -        -    2  2  2  2        0       0
 3 -   0.0400W       -        -    3  3  3  3      210    1200
 4 -   0.0050W       -        -    4  4  4  4     2000    8000

Supported LBA Sizes (NSID 0x1)
Id Fmt  Data  Metadt  Rel_Perf
 0 +     512       0         0

=== START OF SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

SMART/Health Information (NVMe Log 0x02, NSID 0xffffffff)
Critical Warning:                   0x00
Temperature:                        41 Celsius
Available Spare:                    100%
Available Spare Threshold:          10%
Percentage Used:                    0%
Data Units Read:                    3,597,546 [1.84 TB]
Data Units Written:                 4,957,883 [2.53 TB]
Host Read Commands:                 50,160,797
Host Write Commands:                12,346,245
Controller Busy Time:               106
Power Cycles:                       105
Power On Hours:                     107
Unsafe Shutdowns:                   10
Media and Data Integrity Errors:    0
Error Information Log Entries:      0
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0
Temperature Sensor 1:               41 Celsius
Temperature Sensor 2:               44 Celsius

Error Information (NVMe Log 0x01, max 64 entries)
No Errors Logged

```

---

### Post by Jugdish on 2019-01-18
I just wanted to follow up here on the steps that I took next, in case it's helpful for anyone who finds themselves in the same situation -- a failing drive containing important data and no backups!

**Stop using the failing drive.** Upon learning that my drive was on its last legs, I immediately shut it down and did not power it on again until I had a replacement drive to clone it to.

**Get a new drive.** The failing drive was a 5-year-old WD Red 4TB. I decided to upgrade to a HGST 6TB. I went with HGST because of its stellar failure record as reported by the [backblaze stats]("https://www.backblaze.com/blog/hard-drive-stats-for-2017/"). This brand is bit more expensive than WD or Seagate, but I found a reasonably priced one on ebay (for new).

**Clone the failing drive.** When the new drive arrived, I hooked it up to my computer next to the old one. I used [GNU ddrescue]("https://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html") to clone the old drive to the new one. To do this, I booted up with an Ubuntu Live CD on a USB stick (I did this instead of booting into my regular system in order to avoid having the drives auto-mounted on startup). To create the bootable USB drive, I used [Linux Live Creator]("https://www.linuxliveusb.com/") (for Windows) with an Ubuntu 18.04 image, and made sure to enable persistent storage on the USB drive (this was necessary so that there was a writeable place to output the important "mapfile" which ddrescue produces).

GNU ddrescue was not included by default with the Live CD, so I had to install it:
```
sudo add-apt-repository universe
sudo apt update
sudo apt install gddrescue
```
I determined the paths to each of the connected drives using: ```
sudo lshw -C disk
```. This told me the old drive was /dev/sda and the new drive was /dev/sdb. So to do the clone I ran: ```
sudo ddrescue -f /dev/sda /dev/sdb ~/mapfile
```This took about 16 hours to clone the 4TB drive. During the clone, 527 read errors occurred in 111 bad areas, amounting to about 220KB of lost data.

**Fix errors on the copy.**  After running ddrescue, I powered down, disconnected the old drive, and laid it to rest. Now with only the new drive attached, I booted up again from the Live CD. This time, I ran ```
sudo fsck -cy
``` on the copied partition in order to fix any outstanding filesystem errors that were cloned over from the old drive. I hadn't run this command on the old drive beforehand because I didn't want to risk killing it with unnecessary I/O load before it had been cloned. In my case, fsck took about 7 hours to run on the 4TB partition and found a few bogus inode entries that it repaired.

**Expand the partition.** Because ddrescue did a block-for-block clone of the partitions on the old drive, and I was cloning from a smaller to a larger drive, I now had a 4TB partition on a 6TB drive, with the rest as unallocated space. This was easily fixed by extending the partiton using gparted. Again this involved booting up with the Live CD. gparted is included by default. Extending the partition did not affect any of the existing data on the drive.

**Update /etc/fstab.** The final step was to update the /etc/fstab file to remove the old drive and register the new drive so it would auto-mount on boot. Note that because ddrescue had cloned everything about the partition, the UUID of the partition copy was the same as the old one, so actually nothing needed to be changed in /etc/fstab, but it was worth spot-checking it anyway.

---

