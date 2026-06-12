---
title: "Bug or RTFM: suddenly read-only disk"
date: 2007-01-08
forum: General Help
---

### Post by sph on 2007-01-08
I cannot decide wether this is a bug or RTFM error.

My setup has two disks one of them has Ubuntu on it and there is empty and also an ext3 partition.

I have this in my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>     <type>  <options>                     <dump>  <pass>
proc            /proc             proc    defaults                      0       0
/dev/hdc3       /                 ext3    defaults,errors=remount-ro    0       1
/dev/hdc2       /media/datastore  ext3    auto,exec,rw                  0       0
/dev/hdc5       none              swap    sw                            0       0
/dev/hdd        /media/cdrom0             udf,iso9660 user,noauto       0       0


I am almost sure that this is correct.

I have created the mountpoint, this user is the owner and the /datastore folder has 777 permissions, not nice but hey I am troubleshooting.
After boot everything works as expected. When I use Nautilus file browser to copy large amounts of data to this folder everything seems to be going OK until there is an error message stating that the disk is read-only.
This is after a large amount of data has already been copied to this particular disk (actually it's a partition, but this is the error message syntax). It looks to me that I can copy a little under 1 GB, about 940 MB. or thereabouts. 
After a reboot everything is nice and dandy until I copy data to it and the same thing happens. 

The other partition is A-OK

I can reproduce this behaviour whenever I want. 

This one has me stifled. I find it pretty hard to believe that permissions can change on the fly while they still appear OK in Nautilus file browser.

The one thing that struck me is that the amount of data that I am able to copy is at or near my total internal RAM memory. Don't know if that means anything.


So what do you think? Is this a bug or should I just Read The Fantastic Manual ?

Regards
SPH

---

### Post by gborzi on 2007-01-08
I don't want to scare you, but I have had a similar problem that was due to HD failure, that I had to change. Just to be sure, install the smartmontools and check your HD.

---

### Post by sph on 2007-01-09
No sooner said then done.

Here's the output:

root@SKYNET:/home/sph# smartctl -a /dev/hdc
smartctl version 5.34 [x86_64-unknown-linux-gnu] Copyright (C) 2002-5 Bruce Alle n
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     HDT722516DLAT80
Serial Number:    VD071CTCD6B25N
Firmware Version: V43OA70A
User Capacity:    164,696,555,520 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 1
Local Time is:    Tue Jan  9 19:49:18 2007 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                 (3385) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off supp ort.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (  57) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_ FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -        0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -        0
  3 Spin_Up_Time            0x0007   185   185   024    Pre-fail  Always       -        186 (Average 191)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -        301
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -        0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -        0
  8 Seek_Time_Performance   0x0005   100   100   020    Pre-fail  Offline      -        0
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -        5201
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -        0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -        243
192 Power-Off_Retract_Count 0x0032   100   100   050    Old_age   Always       -        498
193 Load_Cycle_Count        0x0012   100   100   050    Old_age   Always       -        498
194 Temperature_Celsius     0x0002   189   189   000    Old_age   Always       -        29 (Lifetime Min/Max 14/44)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -        0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -        0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -        0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -        0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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


Disk looks to be A-OK doesn't it?

Any other options, ideas or just plain wild speculations?

---

### Post by gborzi on 2007-01-09
IIRC I used > sudo smartctl -H /dev/hda as was suggested in an howto I found on the net, perhaps from a Gentoo user. One thing I noticed, was that just after bootup the result was, OK, after a while the result was "Backup your data because your disk is about to fail" (or something like this) and the third attempt gave something like "Unable to retrieve SMART data". At that point the disk was read-only. I've read that the kernel automatically remounts in read only mode a filesystem when it gives errors. Did you used the smartctl command after the read-only error message appeared or before ? The result you have posted says that the disk is OK.
As for ideas, I suggest you to look if the BIOS of your computer has an utility to check the disk status.
As for a wild speculation, your copy of Linux acquired self-consciousness, like HAL 9000, and realizing it can't physically harm you it/he decided to make you a little bit nervous.

---

### Post by sph on 2007-01-09
I ran the command from a root terminal wich I think equals the sudo command. Anyway it wouldn't run from my regular account.
I used smartctl when it had changed to the read-only state.

I have tried to copy a large file (2GB) to the folder on that partition and it also failed after a while. Guess how much data it had copied....exactly 1 GB 

I will look at the BIOS although I cannot imagine this to be a disk problem because the other two partitions on the disk namely / and swap are functioning 100% OK.

You might be right about my Linux copy acquireing those kind of characteristics because I have noticed that my system name is changed into SKYNET. It might very well be that is has become selfaware and that doomsday is near. I need Arnie's phonenumber now!!

Regards,
sph

---

### Post by gborzi on 2007-01-09
> **sph said:**
> I ran the command from a root terminal wich I think equals the sudo command. Anyway it wouldn't run from my regular account.
I used smartctl when it had changed to the read-only state.
So the disk seems OK.

> **sph said:**
> 
I have tried to copy a large file (2GB) to the folder on that partition and it also failed after a while. Guess how much data it had copied....exactly 1 GB
Have you checked if there is some limit on the operation you can carry out ? For example, do you have disk quotas configured ? which is the output of ulimit ?
BTW, I tried copying a 1.2 GB file from my home dir to the /usr partition (with sudo) and it worked.

> **sph said:**
> 
You might be right about my Linux copy acquireing those kind of characteristics because I have noticed that my system name is changed into SKYNET. It might very well be that is has become selfaware and that doomsday is near. I need Arnie's phonenumber now!!


I think SKYNET is better than HAL 9000, because if you manage to survive the first two terminators the third one should be a very nice girl.

---

### Post by mdurham on 2007-01-09
There are many posts and bug reports on using Nautilus to copy large amounts of files.
The general consensus of opinion is  "don't use Nautilus to do that". It has problems.
Use 'rsync' or even 'cp' for peace of mind.
Cheers, Mike

---

### Post by sph on 2007-02-22
I accidentely stumbled upon the reason, sort of:
Heres part of the output of the **dmesg** (is used to examine or control the kernel ring buffer) command:

124.527574] Bluetooth: RFCOMM ver 1.7
[  333.083811] journal_bmap: journal block not found at offset 4108 on hdc2 [  333.083819] Aborting journal on device hdc2.
[  333.302574] __journal_remove_journal_head: freeing b_committed_data [  333.302622] __journal_remove_journal_head: freeing b_committed_data [  333.302662] __journal_remove_journal_head: freeing b_committed_data [  333.304272] ext3_abort called.
[  333.304336] EXT3-fs error (device hdc2): ext3_journal_start_sb: Detected abor ted journal [  333.304415] Remounting filesystem read-only [  334.054095] __journal_remove_journal_head: freeing b_frozen_data [  334.054102] __journal_remove_journal_head: freeing b_frozen_data [  334.054105] __journal_remove_journal_head: freeing b_committed_data [  334.054108] __journal_remove_journal_head: freeing b_frozen_data [ 1103.191707] gnash[6358]: segfault at 0000000000000540 rip 00002aaaadd1df39 rs p 000000004087b068 error 4


Soo.. because the filesystem cannot find a journal block on the device it aborts and the consequence of that is the device is remounted read-only .

Question is then why cant it find the journal block. Remember I can reproduce this behaviour at will: after about 1GB has been copied to this disk it remounts read-only. IMHO that means it cannot be a physical defect on the device because of the many cycles of writes, deletes and writes it would happen at a different physical block in those cases.

I am running AMD64 version of Ubuntu and I am wondering whether it could be related to that... in the sense that at the OS or driver level there's something causing this

Anyhow any ideas welcome.

---

### Post by vrix on 2007-04-21
I've been looking for answers regarding this problem since edgy upgrade and also encountered it in feisty, and found this post may help: [http://ubuntuforums.org/showthread.php?t=166826&highlight=journal+offset]("http://ubuntuforums.org/showthread.php?t=166826&highlight=journal+offset")

I just changed /etc/fstab device to ext2 from ext3, and it worked since. I'm still observing the system.
Your post was on february, maybe you could share your ideas on how you solved this. Thanks!

---

### Post by sph on 2007-06-26
I would like to share on how I solved this *if* I had solved it. I just took another parttion on the other harddisk and formatted that with ReiserFS. Not a single problem since. I am using that partition a lot because all my music and video is on there.
I guess I will now have to put ReiserFS on the original problematic partition as well and see how it goes.

The thread you are linking to looks to me giving some soudn tips. I know that by reverting to ext2 I will have no more journal issues because ext2 has no journal. However I want a journalling file system because of the added data safeguards. 

One last question what flavour ubuntu are you running, mine's in my sig. I'd be interested to know wether or not this journal error / read only thing is limited to certain flavours.

anyway have fun

---

### Post by sph on 2007-10-18
I've reformatted the partition in question with ReiserFS and it works like a charm. 
Bit sorry to not have been able to get to the rootcause of this thing but al least we're running on all cylinders again.

Case closed as far as I'm concerned.

Have fun,
sph

---

