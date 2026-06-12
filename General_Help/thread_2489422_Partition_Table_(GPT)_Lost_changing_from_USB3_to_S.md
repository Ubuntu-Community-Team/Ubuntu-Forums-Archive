---
title: "Partition Table (GPT) Lost changing from USB3 to SATA Connection"
date: 2023-07-29
forum: General Help
---

### Post by TheFu on 2023-07-29
Got a new HDD and used a USB3 "Dock" to connect it temporarily to the system for partitioning and LVM configuration.  That went flawless, so I kept going with formatting the logical volumes as ext4 and ran some rsync commands to load up the new disk with data from 10+ yr old disks.

Also, I ran a long SMART test overnight BEFORE doing any LVM just to be certain the HDD looked good.  Passed completely.

What resulted was this:
```
$ sudo parted -lm

BYT;
/dev/sdb:8002GB:scsi:**4096**:4096:gpt:Pluagabl USB3-SATA-U3:;
1:1049kB:8002GB:8002GB::pv-rom01:lvm;

BYT;
/dev/mapper/vg--rom01-lv--rom--export:215GB:dm:4096:4096:loop:Linux device-mapper (linear):;
1:0.00B:215GB:215GB:ext4::;

BYT;
/dev/mapper/vg--rom01-rom--data--r2:1539GB:dm:4096:4096:loop:Linux device-mapper (linear):;
1:0.00B:1539GB:1539GB:ext4::;

BYT;
/dev/mapper/vg--rom01-lv--rom--data--1tb:215GB:dm:4096:4096:loop:Linux device-mapper (linear):;
1:0.00B:215GB:215GB:ext4::;

BYT;
/dev/mapper/vg--rom01-lv--rom--misc--2tb:1649GB:dm:4096:4096:loop:Linux device-mapper (linear):;
1:0.00B:1649GB:1649GB:ext4::;

```

All nice and good. About 3TB of data was copied over too.  All was good.  Modified the fstab to mount the file systems:
```
/dev/vg-rom01/lv-rom-data-1tb  /d/rom/Data/1TB ext4 nofail,noatime,errors=remount-ro 0 2
/dev/vg-rom01/lv-rom-export    /d/rom/export   ext4 nofail,noatime,errors=remount-ro 0 2
/dev/vg-rom01/rom-data-r2      /d/rom/Data/r2  ext4 nofail,noatime,errors=remount-ro 0 2
/dev/vg-rom01/lv-rom-misc-2tb  /d/rom/misc/2TB ext4 nofail,noatime,errors=remount-ro 0 2
```
and tuned some hdparms to get the best read performance. The read-ahead value for the best performance wasn't the typical 256Kb, so this was a good tuning.

Today, I patched the system and during the reboot, moved the HDD from the "dock" internally to a SATA port.  Then rebooted expecting all to be mounted an there for use.  I still need to migrate about 2TB more data over.  The disk is seen, but there's no partition table.  This was a surprise, but because I'd waited overnight, the prior, working, config was saved off.

Anyway, the partitioning looks like this now, but the disk still has all the data!
```
$ sudo parted -lm

BYT;                                                                      
/dev/sdb:8002GB:scsi:_[COLOR="#FF0000"]512[/COLOR]_:4096:unknown:ATA WDC WD8002FZWX-0:;
```

The native blocksize changed from 4096 to 512. Do you see that change?
In an interactive **parted** session, printing the partition table shows this:
```
(parted) p                                                                
Error: /dev/sdb: unrecognised disk label
Model: ATA WDC WD8002FZWX-0 (scsi)                                        
Disk /dev/sdb: 8002GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags: 
```

For fdisk, 
```
$ sudo fdisk  /dev/sdb

Welcome to fdisk (util-linux 2.34).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

GPT PMBR size mismatch (1953506645 != 15628053167) will be corrected by write.
The size of this disk is 7.3 TiB (8001563222016 bytes). DOS partition table format cannot be used on drives for volumes larger than 2199023255040 bytes for 512-byte sectors. Use GUID partition table format (GPT).
```

I really don't have anything to lose since the data is already pseudo-gone, but I'd rather NOT have re-setup all the stuff again and copy the data over. The LVM commands were saved automatically by the lvm.conf file default "save backups", so that really isn't hard. Plus, my daily backups grab everything in /etc/, so the LVM metadata is definitely captured.

Since the problem appears to be at the partition table or higher level, I don't think LVM has anything to do with it.

Would really like to understand why changing from USB to SATA interfaces caused this.  I suspect that the USB3 controller in the "dock" is the problem.  Just appears to be a really stupid problem to me.  Maybe this is just a warning for others, as I doubt any real, practical, solution, exists.

Thoughts?

---

### Post by dragonfly41 on 2023-07-30
Since it is rare indeed for TheFu to start a thread and you contribute so much I thought I would try my pennyworth.
Recently I am increasingly sold on leveraging AI tools as personal research assistants (with human moderation)  so I unleashed my new found AI assistant to hunt for a solution.

The key I have found in these experiments is to boil down the opening query to equivalent of (for readers of a certain age)
“klaatu barada nikto”
[https://en.wikipedia.org/wiki/Klaatu_barada_nikto](https://en.wikipedia.org/wiki/Klaatu_barada_nikto)


One question raised by Robot:
question: What is the make and model of your USB dock? Also, have you tried connecting the drive directly via SATA and observed the same error?

I don't know answer to that question so stopped session at that point.
There must be some useful clues in the torrent of information below. More focussed than Googling.


==============================
**Compressed and derived Query posed to Robot:**


 
On Ubuntu partition table (GPT) is lost when migrating from USB3 to SATA connection in LVM.
SMART test on drive is positive.
 Command - “sudo parted lm”
 returns: 
 
 /dev/sdb:8002GB:scsi:[COLOR=#FF0000]512[/COLOR]:4096:unknown:ATA WDC WD8002FZWX-0:;
 
 The native blocksize changed from 4096 to 512. 
 
 Command - “sudo fdisk  /dev/sdb”
 returns:
 
 "GPT PMBR size mismatch (1953506645 != 15628053167) will be corrected by write.
The size of this disk is 7.3 TiB (8001563222016 bytes). DOS partition table format cannot be used on drives for volumes larger than 2199023255040 bytes for 512-byte sectors. Use GUID partition table format (GPT)".
Explain why changing from USB3 to SATA interface might cause this error?
Could it be USB controller in dock?


**Answer from Robot:**
The issue you are experiencing is related to the way different interfaces handle sector sizes. The GPT (GUID Partition Table) is dependent on the sector size. Some USB enclosures can report 512-byte sectors when the actual sector size is 4096 bytes, or vice versa [unix.stackexchange.com]("https://unix.stackexchange.com/questions/239506/does-the-gpt-partition-table-location-change-when-moving-from-usb3-to-sata"). This discrepancy can lead to the "GPT PMBR size mismatch" error message when transitioning from a USB3 to a SATA connection.


The USB controller in the dock could indeed be a factor in this issue. When the hard drive is connected via USB, the controller might be presenting the drive to the system with a logical sector size of 4096 bytes. However, when the drive is connected directly via SATA, it might report the native sector size, which in your case is 512 bytes [9to5answer.com]("https://9to5answer.com/gpt-pmbr-size-mismatch-will-be-corrected-by-w-rite").


To resolve this issue, you can manually rewrite the partition table while maintaining the start and end sectors the same to avoid data loss. You can use fdisk for this task:
[COLOR=#0e0573]sudo[/COLOR] [COLOR=#0e0573]fdisk[/COLOR] /dev/sdb

Within fdisk:

[LIST]
[*]Use the p command to display current partitions.
[*]Use the g command to create a new gpt disklabel.
[*]Use the n command to add each partition that was previously on the disk. For the First sector and Last sector, enter the values outputted by the earlier p command. Do not remove partition signatures.
[*]Use the w command to write the changes and exit [superuser.com]("https://superuser.com/questions/1352065/gpt-pmbr-size-mismatch-will-be-corrected-by-write").
[/LIST]
Alternatively, you can use gdisk for a more GPT-friendly tool:
[COLOR=#0e0573]sudo[/COLOR] gdisk /dev/sdb

Within gdisk:

[LIST]
[*]Use the p command to display current partitions.
[*]Write down all details (start/end/type of partitions), multiply those 4k-addresses by 8 to get 512b-sector addresses.
[*]Zap the GPT by running sudo dd if=/dev/zero bs=4k count=3 of=/dev/sdb.
[*]Recreate the new GPT with gdisk and the new addresses [unix.stackexchange.com]("https://unix.stackexchange.com/questions/239506/does-the-gpt-partition-table-location-change-when-moving-from-usb3-to-sata").
[/LIST]

Remember to replace /dev/sdb with the actual device identifier for your drive. Also, always have a backup of your data before making such changes.
unix.stackexchange.com > questions > 239506 > does-the-gpt-partition-table-location-change-when-moving-from-usb3-to-sata
[Does the (GPT) partition table location change when moving from USB3 to ...]("https://unix.stackexchange.com/questions/239506/does-the-gpt-partition-table-location-change-when-moving-from-usb3-to-sata")
Can the location of the GPT change when using a different interface (USB, SATA)? Yes, because GPT is stupid and depends on sector size, and..
9to5answer.com > gpt-pmbr-size-mismatch-will-be-corrected-by-w-rite
[[Solved] GPT PMBR Size Mismatch will be corrected by - 9to5Answer]("https://9to5answer.com/gpt-pmbr-size-mismatch-will-be-corrected-by-w-rite")
Solution 2 I had a similar problem when I moved my SATA disk to a USB adapter. Upon starting fdisk: GPT PMBR size mismatch (..
superuser.com > questions > 1352065 > gpt-pmbr-size-mismatch-will-be-corrected-by-write
[GPT PMBR Size Mismatch will be corrected by w (rite)]("https://superuser.com/questions/1352065/gpt-pmbr-size-mismatch-will-be-corrected-by-write")
GPT PMBR size mismatch (1953525167 != 1953525166) will be corrected by write. The backup GPT table is corrupt, but the primary appears OK, so that..
View all search results
=========================================
superuser.com > questions > 1352065 > gpt-pmbr-size-mismatch-will-be-corrected-by-write
[GPT PMBR Size Mismatch will be corrected by w (rite)]("https://superuser.com/questions/1352065/gpt-pmbr-size-mismatch-will-be-corrected-by-write")
[COLOR=#423e3b]GPT PMBR size mismatch (1953525167 != 1953525166) will be corrected by write. The backup GPT table is corrupt, but the primary appears OK, so that..[/COLOR]
9to5answer.com > gpt-pmbr-size-mismatch-will-be-corrected-by-w-rite
[[Solved] GPT PMBR Size Mismatch will be corrected by - 9to5Answer]("https://9to5answer.com/gpt-pmbr-size-mismatch-will-be-corrected-by-w-rite")
[COLOR=#423e3b]Solution 2 I had a similar problem when I moved my SATA disk to a USB adapter. Upon starting fdisk: GPT PMBR size mismatch (..[/COLOR]
serverfault.com > questions > 1125538 > i-get-gpt-pmbr-size-mismatch-error-on-ubuntu-server
[I get GPT PMBR size mismatch Error on Ubuntu server]("https://serverfault.com/questions/1125538/i-get-gpt-pmbr-size-mismatch-error-on-ubuntu-server")
[COLOR=#423e3b]1 Answer Sorted by: 0 This issue is related to the partition table of the hard drive on your Ubuntu system. The message indicates that..[/COLOR]
askubuntu.com > questions > 594767 > gpt-pmbr-size-mismatch-after-dd-clone
[GPT PMBR size mismatch after dd clone - Ask Ubuntu]("https://askubuntu.com/questions/594767/gpt-pmbr-size-mismatch-after-dd-clone")
[COLOR=#423e3b]3 Answers Sorted by: 13 Do as the gdisk prompt suggests: Use the e option on the experts' ( x) menu to relocate the data..[/COLOR]
arstech.net > gpt-pmbr-size-mismatch
[[SOLVED] How to fix error: GPT PMBR size mismatch]("https://arstech.net/gpt-pmbr-size-mismatch/")[COLOR=#423e3b]parted -l parted will ask: Warning: Not all of the space available to /dev/sda appears to be used, you can fix the GPT to use..[/COLOR]
[www.reddit.com](www.reddit.com) > r > linuxquestions > comments > b3pyew > gpt_pmbr_size_mismatch
[GPT PMBR size mismatch : r/linuxquestions - Reddit]("https://www.reddit.com/r/linuxquestions/comments/b3pyew/gpt_pmbr_size_mismatch/")
[COLOR=#423e3b]The solution was simple. I ran gdisk on the bad disk and simply selected the 'w' option. It prompted me a warning, I hit yes,..[/COLOR]
bbs.archlinux.org > viewtopic.php?id=260749
[[SOLVED] GPT PMBR size mismatch when installing / Newbie Corner / Arch ...]("https://bbs.archlinux.org/viewtopic.php?id=260749")

[LIST=1]
[*]1. [COLOR=#423e3b]1. running parted -l 2. it is aware of the problem, and ask "Fix / Cancel" 3. choose Fix 4. Fixed PS: But I still..[/COLOR]
[/LIST]
unix.stackexchange.com > questions > 239506 > does-the-gpt-partition-table-location-change-when-moving-from-usb3-to-sata
[Does the (GPT) partition table location change when moving from USB3 to ...]("https://unix.stackexchange.com/questions/239506/does-the-gpt-partition-table-location-change-when-moving-from-usb3-to-sata")
[COLOR=#423e3b]Can the location of the GPT change when using a different interface (USB, SATA)? Yes, because GPT is stupid and depends on sector size, and..[/COLOR]
github.com > spxak1 > weywot > blob > main > guides > GPT_PMBR_Size_Mismatch.md
[weywot/GPT_PMBR_Size_Mismatch.md at main - GitHub]("https://github.com/spxak1/weywot/blob/main/guides/GPT_PMBR_Size_Mismatch.md")
[COLOR=#423e3b]Now the drive is still reported with the ame number of sectors, but the partition is smaller. We are not done yet. Disconnect SATA, reconnect..[/COLOR]
superuser.com > questions > 410606 > logical-sector-size-changes-depending-on-whether-it-is-attached-via-usb-or-direc
[logical sector size changes depending on whether it is attached via USB ...]("https://superuser.com/questions/410606/logical-sector-size-changes-depending-on-whether-it-is-attached-via-usb-or-direc")
[COLOR=#423e3b]It was driving me nuts, because with the help of testdisk I was able to access the partition, when changing the sector size, but I..[/COLOR]
hddfaqs.com > gpt-pmbr-size-mismatch-will-be-corrected-by-write
[GPT PMBR Size Mismatch will be corrected by w(rite)]("https://hddfaqs.com/gpt-pmbr-size-mismatch-will-be-corrected-by-write/")
[COLOR=#423e3b]Sep 10, 2021 Question: Linux gives error “GPT PMBR size mismatch will be corrected by w (rite).” The error message is far from self-explanatory. Does..[/COLOR]
access.redhat.com > solutions > 5859271
[After building RAID in RSTe mode (IMSM), there will be an error when ...]("https://access.redhat.com/solutions/5859271")
[COLOR=#423e3b]GPT PMBR size mismatch (1781612543 != 1875385007) will be corrected by write. The backup GPT table is not on the end of the device. This..[/COLOR]
superuser.com > questions > 1759323 > a-single-hdd-stops-working-in-usb-2-enclosure
[A single HDD stops working in USB 2 enclosure - Super User]("https://superuser.com/questions/1759323/a-single-hdd-stops-working-in-usb-2-enclosure")
[COLOR=#423e3b]The drive itself works fine (read, write) using another, vertical SATA to USB 3 dock, as well as internal SATA connectors on a fourth machine...[/COLOR]
[www.youtube.com](www.youtube.com) > watch?v=p-uuBGwSB90
[GPT PMBR Size Mismatch USB Drive Problem Fix - YouTube]("https://www.youtube.com/watch?v=p-uuBGwSB90")
[COLOR=#423e3b]This should fix this problem, I am using Ubuntu Linux version 16...[/COLOR]

---

### Post by TheFu on 2023-07-30
Thanks for the reply.  From the links, seems I'm hardly the first person to experience this issue.

It definitely is related to the USB3 Dock controller.

Initially, after connecting via internal SATA, I did rewrite the partition table and **lvscan** did find the LVs, but the VG and PV weren't found.  I was even able to mount the LVs and all the data appeared.  The partition was there, but not marked as LVM2.  So while I could have left it that way, at the next reboot, I suspect everything would have been lost again.  

I needed a fix that was permanent and would make things work every time without any human interaction.  

Late last night, I wiped the drive just to get the idea that I might salvage anything out of my head.  Then I started over with a new partition table, new partitions, new LVM setup that mirrored the old setup and mounted everything.  There was some confusion with 1 LV, it refused to mount.  Because it was Saturday, I could reboot the box, which fixed that issue and proved that the setup performed via SATA was retained between reboots.

Here's what the SATA connected disk looks like this morning:
```
$ sudo parted -lm
BYT;
/dev/sdb:8002GB:scsi:512:4096:gpt:ATA WDC WD8002FZWX-0:;
1:1049kB:8002GB:8002GB:::lvm;

$ \lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
NAME                             TYPE FSTYPE        SIZE FSAVAIL FSUSE% LABEL       MOUNTPOINT
sdb                              disk               7.3T                            
&#9492;&#9472;sdb1                           part LVM2_member   7.3T                            
  &#9500;&#9472;vg--rom01-lv--rom--data--1tb lvm  ext4          200G  185.8G     0% rom-1tb     /d/rom/Data/1TB
  &#9500;&#9472;vg--rom01-lv--rom--export    lvm  ext4          200G  185.8G     0% rom-export  /d/rom/export
  &#9500;&#9472;vg--rom01-lv--rom--misc--2tb lvm  ext4          1.5T   21.4G    94% rom-2tb     /d/rom/misc/2TB
  &#9492;&#9472;vg--rom01-lv--rom--data--r2  lvm  ext4          1.5T    1.4T     0% rom-r2      /d/rom/Data/r2
```

Normally, I'd split the 8TB disk into LVs less than 4TB in size, expanding as needed.  But I'll probably use some of these with different mount options to frustrate crackers. Still, I could simplify from 4 LVs to 2, probably.  Hummmmm.I'm thinking I can merge 3 of those LVs into a single LV.

The AI answers were the same as I'd found, though I don't consider reddit a good source for reputable knowledge. Perhaps that's just my bias. I tried a few yesterday before posting, but the results weren't quite "good" or normal, so I was unwilling to keep them.  Pay now or pay later.  I decided that paying now for a drive that would likely be in service for at least 10 yrs (5 yr warranty) was the correct answer.  I also know that I've never gotten the partition sizes correct, hence the reason to use LVM.

It survived a reboot and came up clean.  The 2TB source was copied over again last night, which took longer than I'd hoped, but seeing 80MB/s writes was good. I think that was probably limited by the source USB hardware with a slow drive.

**If you've seen this problem yourself, please add a "me too" and whatever short description there is time to enter. It would be helpful for others, I suspect.**

---

### Post by dragonfly41 on 2023-07-30
> 
[COLOR=#000000]The AI answers were the same as I'd found, though I don't consider reddit a good source for reputable knowledge.

I don't think that the AI engine has a "trust or reputation vector" as yet. The one I'm trying out in Phind.com which opens a dialogue.  I find that if you define target URL's in the settings you might get more focussed replies.
In fact I have applied it to this forum.  Tested "backup and recovery".

I'm a newbie when it comes to such questions you pose on LVM.

I think that you will beat it in a knowledge match (like a chess game) and it will not pass the Turing test.

I thought that I might get two or more engines talking in a group[/COLOR]

---

