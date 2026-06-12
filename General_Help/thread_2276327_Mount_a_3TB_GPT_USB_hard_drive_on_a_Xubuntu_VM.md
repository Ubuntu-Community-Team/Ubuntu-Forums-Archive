---
title: "Mount a 3TB GPT USB hard drive on a Xubuntu VM"
date: 2015-05-01
forum: General Help
---

### Post by BlackTornado on 2015-05-01
Hello everyone...

I have a quite complicate situation here, and I need some help to come out with a solution.

I have a 3TB USB hard drive with a GPT partition table which contains a lot of data I want to save. The GPT partition was created using a debian server (now dead) and the partitions are ext3 or ext4 (don't remember exactly now).

I only have a laptop running Windows 8, so I installed Xubuntu 14.04.2 on a VMWare virtual machine, I plugged the hard drive into the virtual machine and I was expecting Xubuntu to properly recognize it and mount it.

Obviously, this was not the case.

fdisk complains for not being able to properly handle the GPT partition:

```
WARNING: GPT (GUID Partition Table) d7etected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.
```

I then decided to install GParted, hoping that it could handle the GPT table properly, but that didn't work: it only shows an empty unallocated space of 746,52 GiB.

Finally, I tried a gdisk, and this is the result:

```
GPT fdisk (gdisk) version 0.8.8

Type device filename, or press <Enter> to exit: /dev/sdb
Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Warning! Secondary partition table overlaps the last partition by
4294966385 blocks!
You will need to delete this partition or resize it in another utility.
```

As you can see, I have for some reason an overlapping partition.

I am quite sure the hard drive itself is fine and doing well, but for some reason my installation of Ubuntu can't handle properly the partition table. Any help on how to properly mount the drive?

---

### Post by TheFu on 2015-05-01
Perhaps if you boot off a flash drive and directly access the storage that way you can copy it off? Connect the drive, look at the bottom of **dmesg** output for the partitions. Run **fsck** against them to fix any issues - if that goes well, mount the partitions and copy the data off. Probably want to be root for all this.

**gparted** is THE tool for managing disks.  If you need a CLI tool, use **parted**. Both handle GPT or MBR perfectly.

If you can get the USB passthru working right to the VM, perhaps posting the information that boot-repair gathers would be helpful?  I recall trying to do partition work through USB before and it not working for GPT correctly - the command set for USB isn't the same as the full SATA/eSATA command set for drives.

---

### Post by oldfred on 2015-05-01
Also try parted.
Fdisk does not work on gpt partitioned drives. No need to even try it. Future version may have gpt support.

sudo parted -l

I have seen overlap where it was just a few hundred sectors and delete & recreate partition a few sectors smaller worked.
And I have seen some cases where backup partition table was in middle of drive. Usually from Windows or vendor. Perhaps a vendor dd of a smaller drive configuration onto a larger drive. But either parted or gparted offered to move backup to end of drive.

---

### Post by BlackTornado on 2015-05-02
Thanks to both for the answers... Unfortunately, they didn't solve my problem.

 Booted from a USB drive (to exclude any possible problem with the VM) didn't change anything: gparted still consider the disk to be 746 GiB.

Looks like for some reason the system thinks the hard drive is only 801 GB: even from dmesg, I get this:

```
[   63.488104] usb-storage 2-1.1:1.0: USB Mass Storage device detected
[   63.488356] scsi7 : usb-storage 2-1.1:1.0
[   64.488090] scsi 7:0:0:0: Direct-Access     WDC WD30 EFRX-68AX9N0          PQ: 0 ANSI: 2 CCS
[   64.488389] sd 7:0:0:0: Attached scsi generic sg3 type 0
[   64.489050] sd 7:0:0:0: [sdc] 1565565872 512-byte logical blocks: (801 GB/746 GiB)
[   64.490312] sd 7:0:0:0: [sdc] Write Protect is off
[   64.490315] sd 7:0:0:0: [sdc] Mode Sense: 00 38 00 00
[   64.491675] sd 7:0:0:0: [sdc] Asking for cache data failed
[   64.491678] sd 7:0:0:0: [sdc] Assuming drive cache: write through
```

As the system doesn't seem to recognize all the blocks, the (expected) result is that gdisk thinks I have an partition table that overlaps the size of my disk by 4294966385 blocks, which (at 512 byte each) are exactly equivalent to 2199 GB, precisely what is missing from the 801 GB recognized to make a 3TB disk.

My guess at this point is that the USB controller doesn't handle the 3TB as well as the eSata controller (the hard drive is in a eSata/USB combo enclosure) and was usually connected with eSata.
I will now try to connect the drive trough sata/eSata and see if it works, but if you have any idea in the meanwhile, please shoot!

---

### Post by TheFu on 2015-05-02
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Please post the results from 
**sudo parted -l** and please, please, please use CODE TAGS so things line up for viewing.

---

### Post by BlackTornado on 2015-05-02
Ok... I managed to revive the server where the disk was attached with a fresh installation and plug the disk through e-sata.

Apparently, there are problems with the GPT table even through e-sata, but at least the disk is recognized as 3TB.

```
[   80.851482] ata2.00: ATA-9: WDC WD30EFRX-68AX9N0, 80.00A80, max UDMA/133
[   80.858219] ata2.00: 5860533168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   80.901529] ata2.00: configured for UDMA/133
[   80.905832] ata2: EH complete
[   80.909090] scsi 1:0:0:0: Direct-Access     ATA      WDC WD30EFRX-68A 80.0 PQ                                                         : 0 ANSI: 5
[   80.957119] sd 1:0:0:0: [sda] 5860533168 512-byte logical blocks: (3.00 TB/2.                                                         72 TiB)
[   80.964944] sd 1:0:0:0: [sda] 4096-byte physical blocks
[   80.970990] sd 1:0:0:0: [sda] Write Protect is off
[   80.976419] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, does                                                         n't support DPO or FUA
[   80.986381]  sda:
[   81.051352] GPT:Primary header thinks Alt. header is not at the end of the di                                                         sk.
[   81.058998] GPT:1565565871 != 5860533167
[   81.062947] GPT:Alternate GPT header not at the end of the disk.
[   81.068979] GPT:1565565871 != 5860533167
[   81.072931] GPT: Use GNU Parted to correct GPT errors.
```

Result of parted -l:
```

root@Sheevaplug-sd:~# parted -l
Error: The backup GPT table is not at the end of the disk, as it should be.
This might mean that another operating system believes the disk is smaller.
Fix, by moving the backup to the end (and removing the old backup)?
Fix/Ignore/Cancel?
```

Tried to fix the error... Here is what I get now:

```
root@Sheevaplug-sd:~# parted -l
Model: ATA WDC W[ 1037.011588] uncorrectable error : D30EFRX-68A (scs
[ 1037.015327] end_request: I/O error, dev mtdblock0, sector 0
[ 1037.022484] __ratelimit: 19 callbacks suppressed
[ 1037.027121] Buffer I/O error on device mtdblock0, logical block 0
i)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  3001GB  3001GB  ext4[ 1037.048953] uncorrectable error :          primary
[ 1037.053334] end_request: I/O error, dev mtdblock0, sector 8
[ 1037.060443] Buffer I/O error on device mtdblock0, logical block 1



[ 1037.068029] uncorrectable error :
[ 1037.071282] end_request: I/O error, dev mtdblock0, sector 16
[ 1037.077150] Buffer I/O error on device mtdblock0, logical block 2
[ 1037.084066] uncorrectable error :
[ 1037.087326] end_request: I/O error, dev mtdblock0, sector 24
[ 1037.093194] Buffer I/O error on device mtdblock0, logical block 3
[ 1037.100809] uncorrectable error :
[ 1037.104097] end_request: I/O error, dev mtdblock0, sector 0
[ 1037.109884] Buffer I/O error on device mtdblock0, logical block 0
[ 1037.117149] uncorrectable error :
[ 1037.120401] end_request: I/O error, dev mtdblock0, sector 0
[ 1037.126181] Buffer I/O error on device mtdblock0, logical block 0
[ 1037.133278] uncorrectable error :
[ 1037.136525] end_request: I/O error, dev mtdblock0, sector 0
[ 1037.142304] Buffer I/O error on device mtdblock0, logical block 0
[ 1037.149372] uncorrectable error :
[ 1037.152646] end_request: I/O error, dev mtdblock0, sector 0
[ 1037.158428] Buffer I/O error on device mtdblock0, logical block 0
[ 1037.165478] uncorrectable error :
[ 1037.168727] end_request: I/O error, dev mtdblock0, sector 0
[ 1037.174508] Buffer I/O error on device mtdblock0, logical block 0
[ 1037.181566] uncorrectable error :
[ 1037.184816] end_request: I/O error, dev mtdblock0, sector 0
[ 1037.190595] Buffer I/O error on device mtdblock0, logical block 0
[ 1037.197626] uncorrectable error :
[ 1037.200878] end_request: I/O error, dev mtdblock0, sector 0
[ 1037.207533] uncorrectable error :
[ 1037.210784] end_request: I/O error, dev mtdblock0, sector 0
[ 1037.219932] uncorrectable error :
[ 1037.223228] end_request: I/O error, dev mtdblock0, sector 0
[ 1037.229645] uncorrectable error :
[ 1037.232956] end_request: I/O error, dev mtdblock0, sector 8
[ 1037.239302] uncorrectable error :
[ 1037.242579] end_request: I/O error, dev mtdblock0, sector 8
[ 1037.248898] uncorrectable error :
[ 1037.252173] end_request: I/O error, dev mtdblock0, sector 8
[ 1037.258492] uncorrectable error :
[ 1037.261761] end_request: I/O error, dev mtdblock0, sector 8
[ 1037.268126] uncorrectable error :
[ 1037.271370] end_request: I/O error, dev mtdblock0, sector 8
[ 1037.277712] uncorrectable error :
[ 1037.280962] end_request: I/O error, dev mtdblock0, sector 8
[ 1037.287297] uncorrectable error :
[ 1037.290545] end_request: I/O error, dev mtdblock0, sector 8
[ 1037.296877] uncorrectable error :
[ 1037.300119] end_request: I/O error, dev mtdblock0, sector 8
[ 1037.306458] uncorrectable error :
[ 1037.309703] end_request: I/O error, dev mtdblock0, sector 0
[ 1037.316038] uncorrectable error :
[ 1037.319286] end_request: I/O error, dev mtdblock0, sector 0
[ 1037.325620] uncorrectable error :
[ 1037.328870] end_request: I/O error, dev mtdblock0, sector 0
[ 1037.336297] uncorrectable error :
[ 1037.339543] end_request: I/O error, dev mtdblock0, sector 0
[ 1037.345877] uncorrectable error :
[ 1037.349126] end_request: I/O error, dev mtdblock0, sector 0
[ 1037.355463] uncorrectable error :
[ 1037.358709] end_request: I/O error, dev mtdblock0, sector 0
[ 1037.365047] uncorrectable error :
[ 1037.368293] end_request: I/O error, dev mtdblock0, sector 0
[ 1037.374631] uncorrectable error :
[ 1037.377876] end_request: I/O error, dev mtdblock0, sector 0
Error: /dev/mtdblock0: unrecognised disk label

Error: /dev/mtdblock1: unrecognised disk label

Error: /dev/mtdblock2: unrecognised disk label
```

For some reason, I am not able to install gptfdisk on this "barebone" debian installation...
```

root@Sheevaplug-sd:~# apt-get install gptfdisk
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package gptfdisk
```

Same goes if I try to install gdisk or fixparts...

Now I hit a wall... Any suggestion?

---

### Post by oldfred on 2015-05-02
We also have seen some USB enclosures that just do not support larger drives. Not quite sure why or which ones. But some users just bought a new enclosure making sure it worked for larger drives and then worked better.

---

### Post by BlackTornado on 2015-05-02
Not my case... The drive has been working with this enclosure forever, albeit with the enclosure connected through eSata and not USB.

---

### Post by oldfred on 2015-05-02
While he calls it gpt fdisk, the packages are gdisk or sgdisk. 

I have not had issues installing gdisk from repository, but have installed fixparts by downloading it from the rodbook's site.

---

### Post by TheFu on 2015-05-02
Those i/o errors - check the cable and reseat the connections - cable and drive in slot.

Other than that, I/O errors aren't good. Bad things happening. I'd get another disk and mirror bits with ddrescue ASAP.

---

### Post by BlackTornado on 2015-05-02
Managed to install gdisk (had to add source repositories for jessie for some reason... I'm running on Squeeze)... Now what is next step?

If it can help, I am pretty sure the disk was just a single large ext4 partition spanning the whole disk... Maybe recreating it from scratch from parted without creating a new file system could do the trick?

About the I/O errors: maybe you're right and it is actually the disk that is failing... Here is a smartctl of the disk... Can someone help me read it?
```
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   192   178   021    Pre-fail  Always       -       5366
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       13
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   085   085   000    Old_age   Always       -       11499
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       12
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       11
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       1
194 Temperature_Celsius     0x0022   112   103   000    Old_age   Always       -       38
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0
```

---

### Post by BlackTornado on 2015-05-04
Solved using TestDisk.

For some reason, the partition table was compromised, and Testdisk was finding a partition of type "MS Data" with a file system ext4.
Changing the partition type to "Linux" allowed to mount the hard drive and copy everything with no hurry.

I will of course still format whenever I get the chance, but so far the disk is working just fine.

---

