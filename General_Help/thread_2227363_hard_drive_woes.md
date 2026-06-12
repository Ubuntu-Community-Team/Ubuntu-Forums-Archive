---
title: "hard drive woes"
date: 2014-06-01
forum: General Help
---

### Post by linuxn00b1 on 2014-06-01
I was running a hard drive with xp and linux mint on different partitions. I had problems before but was able to recover. 
I had an improper shutdown and can't recover this time. After the shutdown I would only get a grub rescue screen, I couldn't boot to any OS. 
I tried to rebuild grub but got some sort of CPU error. I could not even access data on the drive from a live CD. I then tried to use system restore disks from toshiba to reinstall xp. It would look like it's working but at the end it would error out ( error E11B0017). I tried the repair, and I tried clean install options, both didn't work. Fed up I removed the hard drive and put it in an external enclosure now it wont mount. It gives this error:

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read first NTFS_BLOCK_SIZE bytes of potential restart page.
The file system wasn't safely closed on Windows. Fixing.
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to calculate free MFT records: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

I also tried to use windows xp on a diff computer to acces it....nothing.

Is my hard drive dead? I have never seen anything like this. Thank you

EDIT: I just used Gparted and formated the whole drive to Fat32....still won't mount

I figured out that I don't have a MBR so I tried this:

[LIST=1]
[*]Open a terminal and type **sudo su**
[*]Type **apt-get install mbr**
[*]Type **fdisk -l** to find out which device is your flash drive
[*]Type **install-mbr /dev/sdx** (replacing x with your flash device)
[/LIST]

this didn't work the message I got was: No boot signature found.  Use --force to override.
I tried --force then typed the command but that's not a real thing.
I tried --force-all install-mbr.....this didn't work. I can't find how to use --for command. Any info would be helpful

---

### Post by linuxn00b1 on 2014-06-01
just got a hold of test disk. The boot sectors are ok. I have a bad MTF and MTF mirror. Any way to fix this?

---

### Post by linuxn00b1 on 2014-06-08
bump for answer.......anybody have similar experience?

---

### Post by dragonfly41 on 2014-06-08
This page says ...

[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

> 
If both MFT and MFTMirr are damaged and thus cannot be repaired using TestDisk, you might want to try commercial software like Zero Assumption Recovery, GetDataBack for NTFS or Restorer 2000. 


and here ...

[http://icrontic.com/discussion/52450/testdisk-shows-mft-and-mft-mirror-bad-what-next](http://icrontic.com/discussion/52450/testdisk-shows-mft-and-mft-mirror-bad-what-next)

suggests a deep scan in testdisk.

---

