---
title: "Cannot Resize Partition Error"
date: 2023-11-27
forum: General Help
---

### Post by box02-02 on 2023-11-27
Hi.

I expanded my backup ubuntu (22.04) partition from 85gb to 160gb using gparted. 

Then using gparted cut/paste, I pasted my live 85gb onto the newly expanded 160gb backup partition. 

The copy was successful, but when it tried to grow the partition table on the 160gb backup I got a "Cannot resize partition' error. 

I tried this again with expanding the partition size to 100gb and then 90gb. Same message.

I finally resized the partition back to the original 85gb, and the gparted copy completed successfully. So it appears that I can never expand my ubuntu partition. Perhaps the gpt in the ubuntu partition is somehow corrupt ??


```
fdisk -l output
Device     Boot     Start        End   Sectors   Size Id Type
/dev/sda1            2048     718847    716800   350M  7 HPFS/NTFS/exFAT
/dev/sda2          718848   95090687  94371840    45G  7 HPFS/NTFS/exFAT
/dev/sda3        95090688  273348607 178257920    85G 83 Linux
/dev/sda4       430635008 1000214527 569579520 271.6G  5 Extended
/dev/sda5       430637056  640352255 209715200   100G  7 HPFS/NTFS/exFAT
/dev/sda6       640354304  644548607   4194304     2G 83 Linux
/dev/sda7       644550656  854265855 209715200   100G  7 HPFS/NTFS/exFAT
/dev/sda8       854267904  875239423  20971520    10G  7 HPFS/NTFS/exFAT
/dev/sda9       875241472 1000214527 124973056  59.6G  7 HPFS/NTFS/exFAT


```
How can I fix this problem ?

Thanks,

---

### Post by TheFu on 2023-11-27
If the file system being modified is "active", then gparted can't alter it.  Usually, that means the method to modify it would be to boot from alternate media (a USB flash version of Linux), ensure it isn't mounted, and use the version of gparted on that flash version of Linux to modify the internal storage.

It appears you are using MBR/MSDOS partition tables. That type of partition table allows access only to 2TB of storage. There are other issues too.  The fix is to use GPT instead which doesn't suffer from that limitation, doesn't require "extended primary partitions" and doesn't limit the number of primary partitions to 4.  It isn't possible to expand storage in a "logical partition" without it being contiguous and wholly contained inside the "Extended partition".  

Whenever posting terminal output, please, please, wrap that output in forum "code tags" so the columns line up. Make it easier for people to help you, please.

This is one of the few times that an _image_ of the _**Gparted**_ layout of the disk would be helpful.

---

### Post by box02-02 on 2023-11-27
I always boot from a gparted usb whenever I adjust partition sizes.

I though I was gpt. What makes you think its mbr/msdos ?


I was trying to expand the 85gb "ubu LIVE" into the additional 75gb unallocated space:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293128&stc=1[/IMG]


Thanks,
M...

---

### Post by box02-02 on 2023-11-27
It does seem like I'm not using GPT. A partition table scan says I am "MBR only" and "GPT: not present". And here is me thinking I was GPT.

 Could this be my problem ?


What is the step by step procedure to convert to gpt ?

 I would do a backup first, and boot from a gparted or ubuntu usb.

Thanks,

M..

---

### Post by TheFu on 2023-11-28
> **TheFu said:**
>  
This is one of the few times that an _image_ of the _**Gparted**_ layout of the disk would be helpful.

Need to see the disk layout image.

---

### Post by MAFoElffen on 2023-11-28
@TheFu -- Image of disk layout in GParted is in Post #3.

"*Warning Will Robinson. Warning.*"

He is dual-boot with Windows installed a Legacy Boot. Ubuntu will boot Legacy from a GPT partitioned Drive. Windows will not.

Have him do
```

sudo dmidecode -t 0 | grep -i 'boot\|UEFI\|legacy'

```
That will tell you he has options, or if he is stuck with an MS-DOS partition table. (Because Windows and it's boot restrictions.)

Here is the type of data that will return:
```

mafoelffen@Mikes-B460M:/data/ISO$ sudo dmidecode -t 0 | grep -i 'boot\|UEFI\|legacy'
        Boot from CD is supported
        Selectable boot is supported
        USB legacy is supported
        BIOS boot specification is supported
        UEFI is supported

```

---

### Post by yancek on 2023-11-28
> I though I was gpt. What makes you think its mbr/msdos ?
 

The gparted image you posted in post 3 clearly shows /dev/sa3 is an Extended partition and that is all you need to see.  GPT partitions do not have Extended partitions, all are primary. If you had posted the complete output of the fdisk command, it would also have shown there as Disklabel type.  This part of the fdisk output would also show the total sectors so you could determine how much room if any, you have on which to expand.  

If /dev/sda3 is  the partition you want to expand, you have room to do that since it ends at sector 273348607 and /dev/sda4 begins at sector 430635008 which leaves you with 157286401 sectors to expand.  To get an approximate size in GB, you do simple math by dividing the total sectors by the size of the drive in GB to get sectors per GB.  You didn't post the complete output of fdisk so we don't know the total sectors so just use a calculator.


>  The copy was successful, but when it tried to grow the partition table on the 160gb backup

How large did you try to make it?  Probably because there isn't room to make it much larger, you'll need to do the math.  

>  I  was trying to expand the 85gb "ubu LIVE" into the additional 75gb unallocated space:


The above quote is from your post 3, note the key icon next to sda3?  That means it is 'locked' or mounted and can't be changed until unmounted even if you are using gparted on an usb, you need to verify partitions you want to modify are not mounted.

> I pasted my live 85gb  

What does the 'live' part mean?  I know you had another thread related to this but don't recall what you were doing.

---

### Post by TheFu on 2023-11-28
> **MAFoElffen said:**
> @TheFu -- Image of disk layout in GParted is in Post #3.
 

I was hoping to see visually where the free space really was located.

As Yancek says, the math is probably off just a tiny bit.  Instead of 75G, try 74G ... or just use the slider in the GUI part of gparted that hasn't been posted.  Gparted does allow us to grab at the ends of each partition and slide it left/right for resizing of known file system types.

Doing much more than that, like anything that alters the existing partition order will likely break one of the OS installs.

On systems with lots of partitions like above, I'd do things differently, but without understanding the whole intend and purpose it is hard to say.

GPT or MBR doesn't matter to Linux boots.  But it does to MSFT. MSFT made some arbitrary choices - "Legacy Boot = MBR" and "UEFI Boot = GPT".  99.999999% of the time, it is best to have all OSes on a single computer boot in the same matter (UEFI or Legacy).

---

### Post by MAFoElffen on 2023-11-28
I see his logical partition /dev/sda3 within the extended partition /dev/sda4, as well as the unallocated space within that. I see /dev/sda3 as mounted. Once he unmount's that, as TheFu said, he should be able to grab the edge of the partition in the graphical representation of it, were it was cutoff above what was posted... and slide it fully to the side, to fill the unallocated space.

The only thing that is stopping that is that it was mounted.

Converting it to GPT takes some heavy lifting. Means getting a very good backup before you start... Because the process may fail and you risk loosing everything. There are one methods. Starting with Windows 10, there is a Windows utility called "MBR2GPT.exe", where that utility will convert from MBR to GPT without having to delete any of the partitions to do it (the data stays)... but you have Windows 8.1, so that will not work.

Here is MS'es instructions:
RE:
[https://learn.microsoft.com/en-us/windows-server/storage/disk-management/change-an-mbr-disk-into-a-gpt-disk](https://learn.microsoft.com/en-us/windows-server/storage/disk-management/change-an-mbr-disk-into-a-gpt-disk)

You can also do it from GParted, which also destroys the data on the disk...
[https://www.diskpart.com/articles/gparted-convert-mbr-to-gpt-4125.html](https://www.diskpart.com/articles/gparted-convert-mbr-to-gpt-4125.html)

Either: Then you restore and get both your OS'es to boot from the EFI partition that you have to create onto in the root of the disk. Long tedious process, but well worth it in the long run.

Easier is to backup all your data... Add a new GPT partition table. Install both OS'es as new/fresh. Then restore your data to each new OS. This migration would be what I would recommend for what would give you the most value for the future.

*** That all assumes that you computer can boot from UEFI. If not, then if you want to keep Window 8.1, then you are stuck with MBR partition with legacy BIOS booting. That is why I asked you to post the output of those commands, to see what it's capabilities are.

Sorry, the cold hard facts.

---

### Post by box02-02 on 2023-11-28
[COLOR=#8b4513]*"How large did you try to make it? Probably because there isn't room to make it much larger, you'll need to do the math."*[/COLOR]
I dragged the slider to the max which is +75gb. That failed so I dragged it to +10gb and that failed as well. I tried lesser values as well. I don't believe this is a space problem - in my humble opinion the FAT for the ubuntu partition has some sort of problem which prevents me from expanding the partition - even by one byte. I'm going to try shrinking the ubuntu partition and see if that works.  

"[COLOR=#8b4513]Instead of 75G, try 74G"[/COLOR]
I did try try lesser values than 75. But I don't see why I can't use the maximum space available to me ?

sudo dmidecode -t 0 | grep -i 'boot\|UEFI\|legacy'
        ```
Boot from CD is supported
        Selectable boot is supported
        USB legacy is supported
        BIOS boot specification is supported
        UEFI is supported
```


[COLOR=#8b4513]"The above quote is from your post 3, note the key icon next to sda3? That means it is 'locked' or mounted and can't be changed until unmounted even if you are using gparted on an usb, you need to verify partitions you want to modify are not mounted."[/COLOR]
The snapshot from gparted was made on the 'fly' when I was writing this post. When I tried the expansions they were done from a booted gparted usb. The partition was not locked.

[COLOR=#800000]"What does the 'live' part mean?"[/COLOR]
I refer to my active ubuntu desktop partition as 'live'. I also have 'backup' ubuntu partitions on other ssd's.


I'm going to try a gparted cut/paste from another partition (other than the ubuntu one) and then see if I can expand it. If I can expand it, that will tell me that the problem is specifically related to the FAT of the ubuntu partition. Does this make sense ?

I'll be back and thanks,
M...

---

### Post by TheFu on 2023-11-28
File systems that are "in use" can't be modified.  Don't mount them and then you can resize with contiguous space, especially to the right.

---

### Post by MAFoElffen on 2023-11-28
And using GParted to copy a partition "that is mounted" is not wise. It's not like doing a Snap Shot. You copied a filesystem that is in an opened state. Which has a high risk of being failed when you paste it somewhere...

+1 with TheFu -- Show us the whole screen of GParted!!! Then we can evaluate what you have and what can be done to it. I'm not going to guess what you have anymore. Too many variables of that can exist.

---

### Post by box02-02 on 2023-11-28
I'm back.

 FYI both the source and destination ssd's are 512gb SATAs.


So **Booting from a gparted usb** with **NO** drives mounted:

I tried to Shrink the destination ubuntu partition and I got the same error as when I tried to expand it.

I then gparted cut/paste from a **different** source partition (not from the 'ubuntu live') to the destination ubuntu partition, and had NO trouble expanding the destination ubuntu partition.

To summarize - if I gparted copy my 'ubuntu live' 85gb partition to a another 85gb partition located on another ssd, I am **unable** to expand or shrink that partition. IMHO, that tells me that the FAT (ext4 file system ?) has a problem on the source 'ubuntu live' partition. 

So I have 3 questions:

1. Where is the File Allocation Table located ? Is it in the partition itself or at the beginning of the SSD right after the boot block ?

2. Is there any way to VIEW the FAT on the partition in question ?

3. Is there any way to REPAIR the FAT on the partition in question ?

Please see my next post for a complete picture of my gparted devices. I can't seem to insert an image on this edit. 


Any info will be greatly appreciated.

Thanks,
M...

---

### Post by box02-02 on 2023-11-28
I'm back once again.

Here is my gparted snapshot. Please note this is a snapshot of my system now, as opposed to when I boot with my gparted usb. 

Please ignore the fact that drives are locked in this snapshot:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293129&stc=1[/IMG]

---

### Post by TheFu on 2023-11-28
See those "key" icons next to the device names?  Those are mounted and cannot be modified.
Boot from a flash drive - an Ubuntu Install Flash drive in "Try Ubuntu" Mode is the normal method.  Until you do that, you can forget about modifying sda3 or sda5.  Also, sda5-sda9 all must fix inside sda4.

I don't see any FAT involved in the image above.  FAT is for MS-DOS, so you'll need MS-DOS tools to deal with it.
NTFS is for MS-Windows.  You'll need MS-Windows to handle any issues with NTFS file systems.
Only sda3 and sda6 can be "fixed" using Linux.

---

### Post by box02-02 on 2023-11-28
> **TheFu said:**
> See those "key" icons next to the device names?  Those are mounted and cannot be modified.
Boot from a flash drive - an Ubuntu Install Flash drive in "Try Ubuntu" Mode is the normal method.  Until you do that, you can forget about modifying sda3 or sda5.  Also, sda5-sda9 all must fix inside sda4.

I don't see any FAT involved in the image above.  FAT is for MS-DOS, so you'll need MS-DOS tools to deal with it.
NTFS is for MS-Windows.  You'll need MS-Windows to handle any issues with NTFS file systems.
Only sda3 and sda6 can be "fixed" using Linux.

Please Mr TheFU - READ MY #13POST above. I specifically say that I boot from a gparted usb and **no drives are mounted** when I attempt to expand the partition.

Thanks,
M...

---

### Post by TheFu on 2023-11-28
> **box02-02 said:**
> Please Mr TheFU - READ MY #13POST above. I specifically say that I boot from a gparted usb and **no drives are mounted** when I attempt to expand the partition.

Thanks,
M...

Something is mounting them.  It is possible, in default desktop configurations, that just a mouse click in a file manager would mount them.  Use the 'mount' command, without any options to see.  You'll probably want to filter on specific device names using grep.  For example, 

```
$ mount | egrep 'sd[a-z]'
```

Or, perhaps the file systems are corrupted, but that would normally show an error in the logs and would prevent any mount.  **fsck** for native Linux file systems can usually correct logical issues.  It works best and quickest with file systems that have journaling. File systems without journaling will take longer and may not be recovered.

Physical problems, which all storage media will eventually have are completely different matters.

---

### Post by MAFoElffen on 2023-11-28
So my questions are:
Which partition are you trying to grow? /dev/sda5? Which looks like that is ntfs and a logical partition...
Is /dev/sda3 a logical or primary partition? It looks like Primary.
Is the unallocated space left of /dev/sda4 The extended partition which all the logical partitions reside?

If my assumptions are correct... Then first grow the extended partition to it's full size... then jump over to Windows, and use Disk Management to grow the NTFS partition, which shows up there as /dev/sda5...

If you use GParted to grow an NTFS partition, it breaks the Widows indexes, and they have to be rebuilt... 

If my assumptions are wrong, then "nevermind."

---

### Post by box02-02 on 2023-11-29
Okay all is fixed :).

By a series of expand/shrink and restoring the ubuntu partition from the backup, I managed to fix the problem. I could not reproduce what I did.

All appears fine, however, gparted 'check' yields an error. so I did an e2fsck:

sudo e2fsck -n -f -v /dev/sda3 (does in fact yield errors):
```
e2fsck 1.46.5 (30-Dec-2021)
Superblock last mount time is in the future.
    (by less than a day, probably due to the hardware clock being incorrectly set)
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  

Inode 398856 was part of the orphaned inode list.  IGNORED.
Inode 405181 was part of the orphaned inode list.  IGNORED.
.....
....
Deleted inode 423935 has zero dtime.  

Pass 2: Checking directory structure
Symlink /home/mg/snap/snap-store/959/.config/autostart/ubuntu-software-service.desktop (inode #5505077) is invalid.

Entry 'ubuntu-software-service.desktop' in /home/mg/snap/snap-store/959/.config/autostart (5505076) has an incorrect filetype (was 7, should be 0).

Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

Free blocks count wrong (21820326, counted=21801533).

Inode bitmap differences:  -398856 -405181 -412803 -413888 -413905 -419605 -419694 -420754 -422367 -423935 -424000 -424415 -427123

Free inodes count wrong (9595312, counted=9594388).

Ubu_Live: ********** WARNING: Filesystem still has errors **********

```

Then I did a: sudo e2fsck -p -v /dev/sda3 to repair any problems and finally the gparted 'check' ran clean.

Note: I noticed that the ubuntu EXT4 partition was Mounted On:   /, /var/snap/firefox/common/host-hunspell
Apparently no harm, but I did a: *sudo snap disconnect firefox:host-hunspell*
and that cleared that up.

Final gparted pic with ubuntu partition grown from 85gb to 160gb
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293135&stc=1[/IMG]


It's all good. Thanks for all your input.
M...

---

### Post by TheFu on 2023-11-29
I use **fsck**, not any other program.  Never understood why people use the others when fsck does the right thing with 1 option.

---

### Post by box02-02 on 2023-11-30
Hi.

Fsck & e2fsck are the same:
[URL="https://superuser.com/questions/19982/what-is-the-difference-between-fsck-and-e2fsck"]https://superuser.com/questions/19982/what-is-the-difference-between-fsck-and-e2fsck
[/URL]
M....

---

