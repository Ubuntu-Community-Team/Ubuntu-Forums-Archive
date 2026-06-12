---
title: "Error mounting system-managed device"
date: 2014-03-13
forum: General Help
---

### Post by billy_kailas on 2014-03-13
Hello everybody.

First of all let me state clearly that i am a noob in linux. 

I have an Acer 6930ZG laptop which originally had two patritions in its disk, one with Vista and one for storage, "DATA", both ntfs. I installed ubuntu 13.04 in the vista partition, kept using the other for storage and everything worked fine until i tried to install the latest nvidia driver from their site. Probably my bad(?) because there has been a kernel update recently. Then i installed 13.04 again on the same partition but now the second partition cant be mounted and i get this error message
[ATTACH=CONFIG]251109[/ATTACH]

I did some research and found this  [http://ubuntuforums.org/showthread.php?t=1688937](http://ubuntuforums.org/showthread.php?t=1688937) but i think it is way more complicated than what i want since it involves dual OS, different bootloaders etc and i didnt get what the solution was. I just want to mount the partition and use it as storage without losing my files.

sudo blkid outputs this

```
billy@billy-PC:~$ sudo blkid
/dev/sda1: UUID="197340b2-f58d-4bb5-b1c4-26eafbe20bea" TYPE="ext4" 
/dev/sda2: LABEL="DATA" UUID="FC54D24254D1FF78" TYPE="ntfs" 
/dev/sda3: UUID="1c614f81-d62f-4a9a-a0f4-0fd50f29354d" TYPE="swap"
```

sudo fdisk -lu outputs this

```
billy@billy-PC:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00042005

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   256780287   128389120   83  Linux
/dev/sda2       256780288   480964607   112092160    7  HPFS/NTFS/exFAT
/dev/sda3       480964608   488394751     3715072   82  Linux swap / Solaris
```


sudo parted -l outputs this

```
billy@billy-PC:~$ sudo parted -l
Model: ATA Hitachi HTS54322 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system     Flags
 1      1049kB  131GB  131GB   primary  ext4            boot
 2      131GB   246GB  115GB   primary  ntfs
 3      246GB   250GB  3804MB  primary  linux-swap(v1)
```

fstab looks like this

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=197340b2-f58d-4bb5-b1c4-26eafbe20bea /               ext4    errors=remount-ro 0       1
# /media/DATA was on /dev/sda2 during installation
UUID=FC54D24254D1FF78 /media/DATA     ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda3 during installation
UUID=1c614f81-d62f-4a9a-a0f4-0fd50f29354d none            swap    sw              0       0


I suppose that the answer is somethere in the above but i cant see it.:confused::confused:


Thank in advance

---

### Post by billy_kailas on 2014-03-18
I ran sudo ntfsfix /dev/sda2 and this is the output

```
billy@billy-PC:~$ sudo ntfsfix /dev/sda2Mounting volume... ntfs_mst_post_read_fixup_warn: magic: 0x6f2d6366  size: 4096   usa_ofs: 26740  usa_count: 29284: Invalid argument
Actual VCN (0x322d353232303231) of index buffer is different from eaxpected VCN (0x3).
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
ntfs_mst_post_read_fixup_warn: magic: 0x6f2d6366  size: 4096   usa_ofs: 26740  usa_count: 29284: Invalid argument
Actual VCN (0x322d353232303231) of index buffer is different from expected VCN (0x3).
Remount failed: Input/output error

```


Anybody??

---

### Post by billy_kailas on 2014-03-25
Hello again, 

I continued to search and found this post [http://ubuntuforums.org/showthread.php?t=2171003](http://ubuntuforums.org/showthread.php?t=2171003),  created a Windows Recovery Disc from a laptop with Win 8 and UEFI (don't have another with BIOS). Unfortunately i got a "Non System Disk" error. Maybe a conflict between UEFI and BIOS? 

After that i downloaded Minitool Partition Wizard boot CD which looks very good and powerful tool, with all the pros and cons that come with that, regarding these kind of programs :). For some reason that i don't know the Check Disks option was not available to me. So i tried the Partition Recover Wizard but it didn't fix my problem. Nonetheless it probably changed something, for the better or for the worse, because now i get a slightly different error message when i try to mount the partition in Ubuntu. 

[ATTACH=CONFIG]251469[/ATTACH]


One good thing is that my files are still on the disc. I browsed the with Minitool Partition Wizard boot CD. Now i am thinking to try the Allign Partition from Minitool Partition Wizard boot CD but i don't understand exactly what it does and i don't want to destroy my data.

Please help!!!!

---

### Post by billy_kailas on 2014-04-10
Hello again, 

I am wondering if anybody reads what i am writing, but i found a solution to my problem and i will post it, hoping to be helpful for someone else in the future. 

I used the command "dd" which performs a low level back up and more specific [COLOR=#000000]"dd if=/dev/sda2 of=/dev/sdc" which backed up everything from my damaged partition to a USB external drive. WARNING [/COLOR][COLOR=#000000]"dd if=/dev/sda2 of=/dev/sdb" deletes all the data, which may exist on the destination drive. Then i plugged in the USB drive to a windows pc and executed "chkdsk /f" which fixed everything. Then i formatted my damaged partition and pasted my data.

One another solution i think would work, would be to format my damaged partition and try to recover the data with testdisk or another data recovery software.[/COLOR]

---

