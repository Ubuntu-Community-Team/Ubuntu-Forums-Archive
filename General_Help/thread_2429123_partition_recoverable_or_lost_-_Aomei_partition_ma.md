---
title: "partition recoverable? or lost - Aomei partition manager"
date: 2019-10-13
forum: General Help
---

### Post by JamButty on 2019-10-13
I have/had a dual boot with an unmovable/unshrinkable (by normal methods) Windows partition. I wanted to take most of the Windows partition, which was seldom used and reallocate it to the ext4 Ubuntu partition. I used freeware called Aomei partition manager, advertised as being specifically tailored to get around the unmovable partitions pre-loaded Windows machines come with. I thought there was a chance I might screw up the Windows partition I was shrinking, but that would ok. Instead, I have the shrunk partition that Windows is/was on and the two ext4 partitions (Ubuntu and a backup partition) merged together as "unallocated space". The Aomei program seems to have taken the two partitions it could not read and, without prompts/warning or any message, just lumped them together.
Right now I only have a grub prompt on boot, which I cannot do anything with afaik. I probably am screwed with both my system and its backups gone. Reloading both the Windows and Ubuntu OSes would be fine, but if that backups partition got wiped - that is a huge loss. 
 I am hoping someone there can correct me on that and advise how to recover my data.

thank you

---

### Post by oldfred on 2019-10-14
Windows has had that issue since Windows 7 and thru Windows 10. It "forgets" to write Linux partitions back to partition table. But data is still there.

Do you know partition sizes or better details by sector? Then relatively easy to add partition(s) back into partition table.

backup current partition table before any changes, so you can get back to current if changes not correct. Save to another device.
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print

You can use testdisk or parted rescue. With two partitions may be a bit more difficult as you have to find two starts & two ends that do not overlap.

Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988) &
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[https://www.gnu.org/software/parted/manual/parted.html#rescue](https://www.gnu.org/software/parted/manual/parted.html#rescue)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition](https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition)

---

### Post by JamButty on 2019-10-14
Thanks! I will spend the day with this. Coffee on!

---

### Post by JamButty on 2019-10-14
Ok, I have sectors info written out to thumbdrive, but I don't follow how I can determine the start/end points of the missing partitions when the system does not acknowledge they exist. The missing chunk is between Sda3 and 4. "unallocated space" of 1.7 TB is comprised of ~700Gb taken from prior Windows basic OS partition, ~800Gb Ubuntu and ~200Gb backups.
```
$ sudo sfdisk -d /dev/sda
label: gpt
label-id: D7DEC1ED-6E75-47D5-9EFF-1B5C73DFE06B
device: /dev/sda
unit: sectors
first-lba: 34
last-lba: 3907029134

/dev/sda1 : start=        2048, size=     1024000, type=C12A7328-F81F-11D2-BA4B-00A0C93EC93B, uuid=B981DB20-5BF0-4DA9-AB1D-6A1E9C0714D6, name="EFI system partition"
/dev/sda2 : start=     1026048, size=      262144, type=E3C9E316-0B5C-4DB8-817D-F92DF00215AE, uuid=DAD83CF7-6D09-422E-BD63-F8E381AE162F, name="Microsoft reserved partition"
/dev/sda3 : start=     1288192, size=   629150602, type=EBD0A0A2-B9E5-4433-87C0-68B6B72699C7, uuid=A03B89A5-251D-48EC-9DC9-73ED70EA91B2, name="Basic data partition"
/dev/sda4 : start=  3881201664, size=      921599, type=DE94BBA4-06D1-4D40-A16A-BFD50179D6AC, uuid=5875B576-2A94-4E54-90B3-37D7BDE632F1, attrs="RequiredPartition"
/dev/sda5 : start=  3882123264, size=    24905727, type=DE94BBA4-06D1-4D40-A16A-BFD50179D6AC, uuid=CC7E648A-2A59-4FC7-8E29-C793CD33735B, attrs="RequiredPartition"

```
```
$ sudo parted /dev/sda unit s print
Model: ATA ST2000DM001-1ER1 (scsi)
Disk /dev/sda: 3907029168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start        End          Size        File system  Name                          Flags
 1      2048s        1026047s     1024000s    fat32        EFI system partition          boot, esp
 2      1026048s     1288191s     262144s                  Microsoft reserved partition  msftres
 3      1288192s     630438793s   629150602s  ntfs         Basic data partition          msftdata
 4      3881201664s  3882123262s  921599s     ntfs                                       hidden, diag
 5      3882123264s  3907028990s  24905727s   ntfs                                       hidden, diag


```


I have never used Testdisk before. Perhaps it can sort out where the partition markers should go. But I don't understand how to install that. Normal install not working. (I am on the install disk-try temporary environment)


```
$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: Unable to locate package testdisk

```
```
$ testdisk --version

Command 'testdisk' not found, but can be installed with:

sudo apt install testdisk

```
apt or apt-get, same result


edit:ok now. Universe repository was not enabled. proceeding with testdisk.

---

### Post by oldfred on 2019-10-14
Since you have gpt, and Windows often forgets to update backup gpt partition table, does this show a mismatch and then you can restore from backup partition table?
sudo gdisk /dev/sda -l
More details on gdisk:

Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update primary, backup & protective MBR. Details:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
[http://askubuntu.com/questions/446991/gparted-claims-whole-hard-drive-is-unallocated-and-gives-warning-about-gpt-table](http://askubuntu.com/questions/446991/gparted-claims-whole-hard-drive-is-unallocated-and-gives-warning-about-gpt-table)

Do you have universe turned on? Perhaps live installer does not have that? 
I never had issues installing testdisk.

I always use synaptic if not using command line, so I can see more details.

Since two partitions, testdisk may work better as it should show multiple deleted partitions. You may have too many options, but want to be sure to include existing partition(s), and the two missing, but if multiple version have to select a set that does not overlap. Testdisk does not know last version, just many old partitions.

Parted rescue is easier, but you have to have some good idea of start & end sectors. When one missing that can often be just the end of last and end of drive or start to a partition after the unallocated space.

---

### Post by JamButty on 2019-10-14
I am pretty confused right now. Testdisk completed analysis, but results make little sense to me, plus there were various errors/warnings along the way like
```
check_part_gpt failed for partition
Error: size boot_sector 629150603 > partition 629150602
No FAT, NTFS, ext2, JFS, Reiser, cramfs or XFS marker
Check the harddisk size: HD jumpers settings, BIOS detection...
The harddisk (2000 GB / 1863 GiB) seems too small! (< 3973 GB / 3700 GiB)
The following partition can't be recovered:
     MS Data               3881201663 7761115134 3879913472
     NTFS, blocksize=4096, 1986 GB / 1850 GiB

```

Most of the possible partitions it listed at the end seemed gibberish. The EFI partition (first one "ESP") agrees with prior "sudo parted /dev/sda unit s print" output. The "Backups" partition seem to be about 231 Gb which is roughly right, it was just over 200 Gb. 
The prior partitions were:
1 EFI (MS)
2.Micosoft reserved
3. MS main OS
4. Ubuntu OS
5. Backups
6. linux swap
7. Winretools (MS)
8. Image partition (MS)

Had it worked correctly, it would be the same plus 700Gb unallocated between 3 and 4. The rest of the final Testdisk output makes no sense at all to me.

```
TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 2000 GB / 1863 GiB - CHS 243201 255 63
     Partition               Start        End    Size in sectors
 P MS Data                     2048    1026047    1024000 [ESP]
 D MS Data                  1288192  630438794  629150603
 D MS Data                  1288192 3881201663 3879913472
 D MS Data                985868448 2954590367 1968721920
 D MS Data               3233509445 3233796367     286923 [^X^D]
 D MS Data               3234163781 3234450703     286923 [^X^D]
 D MS Data               3403610112 3856207871  452597760 [Backups]
 D Linux Swap            3856207872 3881201647   24993776
 D MS Data               3857217537 3882123264   24905728
 D MS Data               3880280065 3881201664     921600
 D MS Data               3881201664 3882123263     921600
>D MS Data               3882123264 3907028991   24905728
Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
                P=Primary  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
ubuntu@ubuntu:~$ 096, 12 GB / 11 GiB


```
I took no action from that point. Testdisk exited while I was trying to figure it out with "SIGINT detected! TestDisk has been killed."

---

### Post by JamButty on 2019-10-14
Testdisk makes no sense to me. I finally chose [Backups] for a "add partition operation, chose Linux LVM (other options were Swap, reserved and Raid, none of which sounded right) and ext4 as the type. What Testdisk presented me with is this
```
TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 2000 GB / 1863 GiB - CHS 243201 255 63
     Partition               Start        End    Size in sectors
 P Linux LVM                      1 3907029167 3907029167
 P MS Data                     2048    1026047    1024000 [ESP]
 D MS Data                  1288192  630438794  629150603
 D MS Data                  1288192 3881201663 3879913472
 D MS Data                985868448 2954590367 1968721920
 D MS Data               3233509445 3233796367     286923 [^X^D]
 D MS Data               3234163781 3234450703     286923 [^X^D]
>D MS Data               3403610112 3856207871  452597760 [Backups]
 D Linux Swap            3856207872 3881201647   24993776
 D MS Data               3857217537 3882123264   24905728
 D MS Data               3880280065 3881201664     921600
 D MS Data               3881201664 3882123263     921600
Structure: Bad. Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
                P=Primary  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
ext4 blocksize=4096 Large_file Sparse_SB, 231 GB / 215 GiB


```
apparently a new partition with no name comprising all 2TB of the disk, with the nice note "structure:bad". No kidding.
changed partition characteristic on that bogus new partion from "P" to "D". continuing "deeper look" option

---

### Post by oldfred on 2019-10-14
Did gdisk show anything?

If you had LVM that is a major complication. That would be one partition with multiple volumes inside it. But no idea how to recover from that.
Most say then best to just reinstall and restore from your backups.

If testdisk sectors are correct for your backup partition, that could be good info for using parted rescue as it can find partition if you have start & end. One user posted that it does not have to be exact, but must be inside the actual sector numbers.

---

### Post by JamButty on 2019-10-14
output of 
sudo gdisk /dev/sda -l
did not give me any new information. I don't have the output from it. Currently testdisk is running in "deeper look" mode, has been running about an hour, probably will run for another 2. If I understood testdisk (that is a big IF), I did not actually write that 2TB LVM partition, but added it as a possibility on the list. The DISKS Ubuntu GUI showed the same partitions as before - all Windows + 1.7gb unallocated. 
When I have made partitions, I have never had to specify other than EXT3 or 4 or NTFS or FAT. The only options were Linux reserved and Swap, both clearly wrong and LVM and RAID, AFAIK, I have never messed with Raid disks so LVM was the only option. Is RAID the default??

Currently there is nothing to backup from (not in the last 4 years or so). My backups are exactly what I am trying to save. They are on the [Backups] partition which the AOMEI partition manager borked, along with the Ubuntu and Linux Swap partitions. Restoring  the Ubuntu OS is easy. Restoring the Windows OS maybe more complicated as I never understood how the main partition and the 4 extra partitions MS requires relate, but that should also be possible. But only on the [backups] partition has all my data reliably.

---

### Post by JamButty on 2019-10-15
Ok, while Testdisk was frustrating and slow (each time I ran it I got more gibberish data - last time on "deep look" mode it even claimed I had a MAC partition. BUT, using the data for the lost [Backups] partition I got from the first run through and plugging that into parted rescue, I am fairly sure I have that partition viably recovered. I will reload Ubuntu OS now and hope for the best
Thank you oldfred!
Will write again and close once both Ubuntu and Windows are back up.

---

### Post by oldfred on 2019-10-15
If you recovered your backup partition with parted rescue then you should be able to recover your other partition as it would be in the unallocated space. Start & end is whatever is before and after that unallocated (or end of drive).

---

### Post by JamButty on 2019-10-19
All normal. Backups partition good. Reloaded Ubuntu. Windows auto-repair and Recovery disc both useless, probably due to the shrunken partition, but a fresh install from a newly downloaded ISO from MS worked. Ubuntu reloaded again and all is happy.

---

