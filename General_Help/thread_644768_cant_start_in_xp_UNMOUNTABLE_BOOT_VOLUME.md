---
title: "cant start in xp UNMOUNTABLE_BOOT_VOLUME"
date: 2007-12-19
forum: General Help
---

### Post by monkeyking on 2007-12-19
Installed 7.10, on an thinkpad r40 laptop.
Did a resize during the installation process.
ubuntu can boot, but windows xp cant.

Tried emergency console,
but chkdsk tells  me something about unrecoverable errors.
But I think it's because the console doesn't see the windows partition.
atleas,

commands like dir, doesn't show my files.

thanks in advance

```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

```

```

sudo fdisk -l
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3387    27206046    7  HPFS/NTFS
/dev/sda2            3388        4795    11309760   83  Linux
/dev/sda3            4796        4864      554242+   5  Extended
/dev/sda5            4796        4864      554211   82  Linux swap / Solaris

```

---

### Post by psusi on 2007-12-19
What EXACTLY does chkdsk say?

---

### Post by monkeyking on 2007-12-19
I can access the data with no problems from ubuntu live cd.
and gparted sees that it is ntfs.

But XP appereantly fails to recognize the drive as ntfs.
I tried running the win xp install, just to see if it sees the partition.
it sees the partition and the correct size,
but doesn't mark it as an ntfs.

```

Microsoft Windows XP(TM) Recovery Console.
The Recovery Console provides system repair and recovery functionality.
Type EXIT to quit the Recovery Console and restart the computer.
[CODE]
C:\>chkdsk
The volume appears to contain one or more unrecoverable problems.
C:\>dir
  Directory of C:\
An error occured during directory enumeration

```
[/CODE]

---

### Post by psusi on 2007-12-19
Wow... what a totally useless error message... but that's par for Microsoft isn't it?

---

### Post by fiddledd on 2007-12-19
TestDisk (it's in the repositories so Synaptic will install it) might fix the problems with NTFS. Actually I used it today on my son's XP box as XP was stuck in a Rebbot loop, it fixed the MFT enough for me to get back into Windows. I know you have a different problem, but might be worth a try.

---

### Post by Paulmd on 2007-12-19
> **monkeyking said:**
> I can access the data with no problems from ubuntu live cd.
and gparted sees that it is ntfs.

But XP appereantly fails to recognize the drive as ntfs.
I tried running the win xp install, just to see if it sees the partition.
it sees the partition and the correct size,
but doesn't mark it as an ntfs.

```

Microsoft Windows XP(TM) Recovery Console.
The Recovery Console provides system repair and recovery functionality.
Type EXIT to quit the Recovery Console and restart the computer.
[CODE]
C:\>chkdsk
The volume appears to contain one or more unrecoverable problems.
C:\>dir
  Directory of C:\
An error occured during directory enumeration

```
[/CODE]



It could be that you really have bad sectors.

I would download Seatools from Seagate, burn it to a CD and boot it. Odds are good, (better than 50%) that you have a bad hard drive.

If the repartitioning just failed for no reason ... this IS why gparted tells you to back up your data. 


Also... check this out. The resolution is at the bottom.

[http://www.techspot.com/vb/all/windows/t-26809-PC-wont-boot--I-think-its-an-NTFS-issue-HELP.html](http://www.techspot.com/vb/all/windows/t-26809-PC-wont-boot--I-think-its-an-NTFS-issue-HELP.html)

---

### Post by psusi on 2007-12-19
Instead of seatools you can also use the smartmontools package in Ubuntu, which works on all drives, not just seagate.  If the problem was bad sectors though, then Ubuntu shouldn't be able to read it either.

---

### Post by az on 2007-12-19
Can Ubuntu access the windows partition?  Often, Linux can read an NTFS partition that window's can't.

You can use Testdisk to try to recover the partition and then use your filesystem normally.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

If that fails, you can try to recover files from the partition without the filesystem.

---

### Post by Paulmd on 2007-12-19
> **psusi said:**
> Instead of seatools you can also use the smartmontools package in Ubuntu, which works on all drives, not just seagate.  If the problem was bad sectors though, then Ubuntu shouldn't be able to read it either.

Seatools works on non-seagate drives.

Bad sectors need not affect the whole area of the disk (they rarely do). Smartmon is only for SMART failure prediction. Passing SMART is no guarantee of an error-free drive.

---

### Post by psusi on 2007-12-20
> **Paulmd said:**
> Seatools works on non-seagate drives.

Bad sectors need not affect the whole area of the disk (they rarely do). Smartmon is only for SMART failure prediction. Passing SMART is no guarantee of an error-free drive.

SMART is what seatools uses.  It provides for collecting a number of statistics from the drive that could be used to evaluate the health of the drive, including temperature, lifetime hours, number of power cycles, and how many and which sectors are bad, and a method to ask the drive to perform an internal scan of the media searching for bad sectors.

---

### Post by Paulmd on 2007-12-20
> **psusi said:**
> SMART is what seatools uses.  It provides for collecting a number of statistics from the drive that could be used to evaluate the health of the drive, including temperature, lifetime hours, number of power cycles, and how many and which sectors are bad, and a method to ask the drive to perform an internal scan of the media searching for bad sectors.

Seatools uses SMART, so do most diagnostic programs, but it also scans the physical disk.  

SMART does not provide you with a list of bad sectors. Nor always, how many sectors are bad. REALLOCATED SECTOR COUNT is NOT the same thing. Nor is the sum of REALLOCATED SECTOR COUNT and UNCORRECTABLE SECTOR COUNT. Sometimes the only way to find bad sectors is to actually run a scan. 

[http://en.wikipedia.org/wiki/SMART#Attributes](http://en.wikipedia.org/wiki/SMART#Attributes)

---

### Post by psusi on 2007-12-20
SMART provides a method to scan the disk for defects, and report where one is found.  You can then optionally start a new scan, requesting that it begin after the first defect.

---

### Post by monkeyking on 2007-12-20
Hi again,
I did a total backup of the contents.
Then i deleted the ext3 partition and the swap partition.

After that I tried the winxp recovery console.

And for some strange reason i could use the ms tools. :)

But it didn't really help, since  the mbr is trashed.
I think the testdisk tool fcked it up.

I did combinations of chkdsk /r, fixmbr, fixboot and bootcfg /rebuild.
But still the harddrive can't boot..


After that I tried installing xp again, on some of the free space,
the xp installation copied all the files over,
but harddrive can't boot.

anyone any ideas?

btw this is fdisk output.

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3387    27206046    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            3388        4500     8935920    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda5            3388        4500     8935888+   7  HPFS/NTFS



```

---

### Post by monkeyking on 2007-12-20
I ended up,
just giving up.

Now everything is repartitioned.
hopefully, ubuntu installer will behave better now...

---

### Post by monkeyking on 2007-12-20
Excately the same error,
I can install xp, and that will work fine,
I can install ubuntu, and that will work fine.

But getting a dual boot system up and running on ibm thinkpad r40 is not possible.

I think the problem is related to the speciel mbr that is used for the restore partition.
Somehow grub doesn'r give the right parameters to grub.

---

### Post by Paulmd on 2007-12-21
> **monkeyking said:**
> Excately the same error,
I can install xp, and that will work fine,
I can install ubuntu, and that will work fine.

But getting a dual boot system up and running on ibm thinkpad r40 is not possible.

I think the problem is related to the speciel mbr that is used for the restore partition.
Somehow grub doesn'r give the right parameters to grub.



Did you check the drive for errors or not? It's important. Putting aside the mini-debate over what does what, it's really important to be sure that your drive is error-free. Especially as we know this is not a one time event.


Now that I know you have an IBM.... you can download IBM's diagnostic tool.

[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-56222](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-56222)

You will have to extract the ISO file from the executable. 7-zip usually works for the "self-extractors".

---

### Post by joeyteetops on 2007-12-21
I'd highly recommend not using that drive for anything moving forward.  When you start to have chunks of bad sectors it's typically the beginning of the end to the slow death march of those old travelstar hard disks (if that's what you have).   Especially if you heard that drive ticking/snapping/rattling when you were trying to access the $MFT.

---

