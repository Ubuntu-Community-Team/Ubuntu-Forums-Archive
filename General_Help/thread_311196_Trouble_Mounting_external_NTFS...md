---
title: "Trouble Mounting external NTFS.."
date: 2006-12-02
forum: General Help
---

### Post by Will5639 on 2006-12-02
About 2 weeks ago my laptop died on me.  Power related difficulties.

But before I can send it in I need to get stuff off and _delete some private information off_.

So I pulled out the HardDrive and hooked it upto my desktop computer with the adapter...  Window's kept giving me delayed write errors so I'm trying to work in Ubuntu.

I followed the "NTFS read/write using NTFS-3g" instructions:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

And it apears to have found my desktop computer's NTFS drives just fine.

But my laptop HD has techniqly become an external.. and I don't understand how to make it mount properly.  It auto-mounts as without ntfs-3g in a readonly environment.

I ran pmount-hal on it and was told an "unclean device".

> root@willis-desktop:/home/willis# pmount-hal /dev/sda1
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) Run 'ntfsfix' on Linux which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.
Error: could not execute pmount


I've finished copying off the important data... but I still need to whipe data off.. WITHOUT whiping the entire drive clean.

---

### Post by Will5639 on 2006-12-02
Weird... is this common [something I'd have to install]???

> ntfsfix: command not found


---

### Post by Will5639 on 2006-12-02
Ok...

Disregard the prior message, sorta.

I got ntfsfix to run, but it fails:

> # ntfsfix /dev/sda1

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

### Post by l:x on 2007-02-16
You might want to boot in Windows and run CHKDSK on the drive:
```
CHKDSK /f /v /r /x <DRIVE>:
```
Eject the drive in Windows using the "Safely remove hardware" icon in your systray.

Otherwise you can use the force option of ntfs-3g (-o force). Make sure you have backed up all necessary data before doing this!

---

