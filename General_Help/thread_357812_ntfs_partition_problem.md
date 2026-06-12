---
title: "ntfs partition problem"
date: 2007-02-10
forum: General Help
---

### Post by mitsuo on 2007-02-10
well.. i have a problem, i cant mount my NTFS partition, which is /dev/sda2
the problem is the journals.. i mean:
> mit@magi:~$ sudo ntfs-3g /dev/sda2 /data 
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) Run 'ntfsfix' on Linux which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.

i would usually boot into windows to fix it up, but i can't, i dont have windows anymore..
and i cant afford myself to format the drive..

another thing is:
> 
mit@magi:~$ sudo ntfsfix /dev/sda2
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr... 
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... FAILED
Error setting volume flags.


---

### Post by mitsuo on 2007-02-10
i am really sorry for my impatience, however, this is a really urgent call..

---

### Post by bmt on 2007-02-10
If you need *urgent* access, then mount it 'ro' (option F).  (I would make a copy of the partition at this point.)

When access is not so urgent and you have more time, try option E.

[This thread]("http://www.ubuntuforums.org/showthread.php?t=217009&page=102") (scroll to message 1015) has someone in a similar position, with comments from better qualified people than me. ;-)

---

### Post by mitsuo on 2007-02-10
well, i have managed to fix it up,
i used an xp installation disk in order to get to the recovery console, and run "chkdsk"
now i get no problems with my drive.
hope it helps someone one day..

---

