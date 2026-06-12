---
title: "Cancelled resizing operation and can't access the partition now"
date: 2021-01-23
forum: General Help
---

### Post by s1mply on 2021-01-23
Hi All,

I'm not sure if I am posting this in the correct thread but here goes. I have 2 drives on my machine. 1 for the OS which is a NVME drive and another I use to store my photos, music, videos etc. I found there was some free space on the secondary drive so I attempted to resize it. Only issue was I cancelled the resize as it was estimated to take 12 hours. Anyway here we stand. Running Fsck on the disk gives the following: 

fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda2

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

Here is the pastebin from boot-repair:
[https://paste.ubuntu.com/p/CnXjF8zQMF/](https://paste.ubuntu.com/p/CnXjF8zQMF/)


Would anyone be able to make any suggestions? 

Kind regards,

---

### Post by ajgreeny on 2021-01-23
I have a suspicion that you did the worst thing you could possibly have done by cancelling an action that had already started on a partition.

However, it is not easy to figure out exactly what you did or what application you used to do it so tell us more in greater detail what you actually did, giving us the proper device names if possible rather than*** "I found there was some free space on the secondary drive so I attempted to resize it."*** which is not very helpful, though I am presuming that was the data drive you speak of, not the OS drive.

Are you still able to use the OS on the disk or did you run boot-repair from a live disk?
It looks as if this report was created from your installed system though the information at the top of the report suggests that you have damaged the partition table or partitions on the disk.

I hope you have backups of the data so that you can restore it if necessary, which I have a feeling may be the case.

---

### Post by s1mply on 2021-01-23
Hey ajgreeny, 

Unfortunately I did this a few days ago, so I apologise for any missing information in advance.  
There are 2 physically separated drives, one has my operating system loaded and that one is absolutely fine, I formatted the whole drive to remove windows and replace it with ubuntu. On the secondary drive, I noticed a partition to tune of 129 mb ( the name and type I cannot recall). I deleted that partition and attempted to expand the data partition using gparted to include the 129. Hence this is where the issue occurred. just a note the secondary drive was always a back up drive with data. I don't have back ups, I know this was really dumb.

---

### Post by tea for one on 2021-01-23
As mentioned by ajgreeny, interrupting a proces involving partitions is often a disaster.

As you do not have backups, all you can do now is try to repair the file system.
[COLOR="#0000FF"]Lines 20 -34[/COLOR] of the report indicate that it **may** be [COLOR="#0000FF"]NTFS[/COLOR]

If it is a Windows file system, you will need Windows tools to attempt the repair.
If it is a Linux file system, then Linux tools are preferred.

Please confirm the file system on your sda drive?

---

### Post by s1mply on 2021-01-23
Hi Tea for one, 

Thank you for the reply, it was a windows partition, when I run testdisk, it shows as EFI GPT. Also I am able to rescue individual files using photorec  if I assign it as a windows partition so that's a sign of hope. 

regards,
Divyesh

---

### Post by yancek on 2021-01-23
You indicate that you deleted a partition of 129MB and tried to add it to  a previouos/continguous partition.  I would not expect that to take more than a minute or two.  Was it actually an already existing partition or was it unallocated space?    What happened when you ran the e2fsck command with the options suggested/recommended by the system? 

Looking at the boot repair output, it shows the problem with sda2 and seems to think this is/was an ntfs partition.  Was it?  If so, why since you have only Ubuntu installed?  If it was/is an ntfs partition you will need to use windows or a windows install/repair disk to fix it.

---

### Post by ajgreeny on 2021-01-23
*Thread moved to **General Help**.* which is more appropriate and a better fit as this was not about installation or upgrading.

---

### Post by oldfred on 2021-01-23
If a NTFS partition, you cannot fully repair from Linux.
Both chkdsk & defrag can only be run from Windows.

And some have posted that Windows tools may work better to recover files from NTFS, but photorec may also work.
The Windows tools may recovery full filename, photorec only recovers by type or file extension, not full name. 
And you need another drive of same size to recovery data to.

With a much smaller drive, it took me overnight to find some text files I lost. Then it recovered every version, in some cased 5 or 6 copies as I had saved many multiple times. It took weeks to compare each file to older backup version. Or now do better backups.

If drive is gpt, and created from Windows, it creates the system reserved partition as first partition. It is not large, so no reason to change. 
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

I would first try testdisk to see if it would see partition in correct place. But the system reserved is unformatted space and often tools move partition into that space corrupting it.
NTFS requires the BS or PBR - partition boot sector to have a NTFS signature. 
Test disk used to be able to recover a PBR, or create a new XP type. But new systems since Windows 7 have a slightly different NTFS BS. Chkdsk from Windows often could then convert it. Windows chkdsk would not run if NTFS BS is blank or damaged, it thinks it is RAW or unformatted.

Windows free recovery software - new 2020 Supports NTFS, FAT, exFAT and ReFS file systems
[https://www.microsoft.com/en-us/p/windows-file-recovery/9n26s50ln705?activetab=pivot:overviewtab](https://www.microsoft.com/en-us/p/windows-file-recovery/9n26s50ln705?activetab=pivot:overviewtab)
An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)

---

### Post by dragonfly41 on 2021-01-23
This is rather messy. I will throw in another idea to add to the advice above.  I understand that you have deleted Windows and you are left with only Ubuntu. You have used Gparted before - although partition resize terminated early. If you return to GParted in toolbar there is an option - Device > Attempt Data Rescue. That might be worth trying on the mangled partition. There is also a package R-Linux in Ubuntu repo which you might try for data recovery.

---

### Post by TheFu on 2021-01-23
No help for this OP, but stuff like this is why all my backups contain the output from **parted -lm**. If anything corrupts a partition table on any disk, there is a copy in the backups to put it back exactly how it was.

Critical data needs 3 copies.  3-2-1 
[LIST]
[*]3 copies
[*]2 different media types
[*]1 remote
[/LIST]

---

