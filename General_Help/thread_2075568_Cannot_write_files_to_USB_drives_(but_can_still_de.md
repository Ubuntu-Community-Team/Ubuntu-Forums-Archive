---
title: "Cannot write files to USB drives (but can still delete files)"
date: 2012-10-24
forum: General Help
---

### Post by gilhornung on 2012-10-24
Hi,

I am an Ubuntu Newbie and I am having trouble with connecting USB drives. Everything was working fine, until recently, when two different drives (SanDisk cruzer 2.0 GB and iOmega 500 GB) had the same problem: When I try to copy files to these drives I get an error "The destination is read-only.". However, I can still delete files that appear on these drives, so they cannot really be read only.

I've tried to format my SanDisk both in Linux and Windows, but that didn't help. I don not want to try and format the iOmega, as this is my backup drive...

I've tried to find an answer in forums and google, but wasn't able to (again, I'm a newbie, so I don't understand all of the technical terms).

Some post with a similar problem asked for the output of sudo fdisk -l, so here it is when the iOmega is connected:
[PHP]Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a9998

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   484806655   242402304   83  Linux
/dev/sda2       484808702   488396799     1794049    5  Extended
/dev/sda5       484808704   488396799     1794048   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xccb5506a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001    7  HPFS/NTFS/exFAT[/PHP]And the last few lines of dmesg:
[PHP]PQ: 0 ANSI: 2 CCS
[379046.308109] sd 25:0:0:0: Attached scsi generic sg2 type 0
[379046.308512] sd 25:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[379046.310249] sd 25:0:0:0: [sdb] Write Protect is off
[379046.310252] sd 25:0:0:0: [sdb] Mode Sense: 28 00 00 00
[379046.311020] sd 25:0:0:0: [sdb] No Caching mode page present
[379046.311023] sd 25:0:0:0: [sdb] Assuming drive cache: write through
[379046.313376] sd 25:0:0:0: [sdb] No Caching mode page present
[379046.313378] sd 25:0:0:0: [sdb] Assuming drive cache: write through
[379046.336563]  sdb: sdb1
[379046.339262] sd 25:0:0:0: [sdb] No Caching mode page present
[379046.339265] sd 25:0:0:0: [sdb] Assuming drive cache: write through
[379046.339268] sd 25:0:0:0: [sdb] Attached SCSI disk
[/PHP]Hope this gives a clue on my problem...

Thanks for the help,

Gil

---

### Post by robert shearer on 2012-10-24
Hi Gil and welcome to the forums.
I have encountered this in other Linux distros and it seems to be as a result of not removing the usb connection without first selecting 'safely remove' or 'eject'.
Occasionally if these drives are used between both Windows and Linux this can arise too.
If you have a Windows install try plugging the drives in, access a file then close and use the safely remove option.
Once removed retry the drive in Linux.

For the flash drive @2GB you may have to copy the files off to some other form of storage (yes, copy, delete etc still work but write seems to be borked) and then reformat the drive and copy the data back.

What to do about the 500GB I do not know but hopefully someone more knowledgable than I will happen along soon...;-)

---

### Post by coldraven on 2012-10-24
I'm no expert but what happens if you right click on the drive? 
If it's shown on the desktop right click on the drive, select properties and then check the permissions.
Or use the file browser and go to /media, find the drive and right click there.
I hope this makes sense :)

---

### Post by Kaheil on 2012-10-24
This may be a "nuclear device" type of solution to a much simpler problem, but you could try the following regarding your USB pen-drive.

First, plug your USB pen-drive into the computer. Then, open your dash ("Windows Key"), search for "Disk Utility" and open it. On the left, there should be a column with "Storage devices". Find your USB device and select it. After making sure you have backed-up all files in it, click on the "Format Drive" option (not to be confused with "Format Partition" one). Selected "Master Boot Record" from the drop-down menu and click "format". If prompted for your password, enter it.

After awhile, you should have a message telling you the operation was successful. Now, on the same menu as before, select the large rectangle (should turn grey) and click "format volume". Choose either NTFS (all systems) or EXT4 (Linux only), give it a cool name (very important) and format the volume. Once done, safely remove the drive and plug it back in. The issue should now be solved.

If you encounter any difficulty in the process, please let us know.

Note: DO NOT DO THIS WITH YOUR EXTERNAL HDD!! THIS OPERATION WOULD WIPE ALL DATA ON THE DISK!!

PS: after writing I realized how "corporate" that sounded. Sorry about that, here is a smile to prove I am human :)

---

### Post by gilhornung on 2012-10-24
Thanks for the reply, robert, cold raven and Kaheil. Great to see support from the community.

Plugging the USB stick to the a Windows computer, and then safely unplugging it, didn't work. It didn't work when I formatted the drive under Windows, too.

According to the permissions I have full access (see screenshot).

When I try to format the USB stick from the Disk Utility program I get an error telling me the the drive is busy (see screenshot). I can still format the drive by right-clicking on the buttons in the left panel, but this type of format doesn't help my problem.

So I guess I'm still stuck. Any other ideas? :confused:

---

### Post by gilhornung on 2012-10-28
Any ideas? Anyone? ](*,)

---

