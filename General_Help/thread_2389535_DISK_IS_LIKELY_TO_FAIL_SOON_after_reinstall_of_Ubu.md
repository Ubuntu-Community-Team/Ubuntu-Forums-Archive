---
title: "DISK IS LIKELY TO FAIL SOON after reinstall of Ubuntu 16.04."
date: 2018-04-18
forum: General Help
---

### Post by Robert_Gaines on 2018-04-18
I reinstalled Ubuntu 16.04 about a month ago, and Ubuntu reported that my secondary hard disk that contains media files was likely to fail soon. This hard disk is for convenience storage only, and all files are backed up onto DVDs. It is also formatted for NTFS to be compatible with other devices, and it kept in my computer's fast swapping drive bay. At any rate, I don't get it because it is has no issues. My opinion is that the Disks utility error message is completely bogus. The fsck just immediately quits when I try to check it with it. I used smartctl, and it indicated that the smart checker was incompatible with the drive. I personally have no idea what that means. I began using modern computers in 2000 back when you were supposed to at least back up often because hard disks rarely gave any warning of an imminent crash. Doesn't Ubuntu just have an equivalent to the scandisk utility in Windows? I have Windows 2000 in VirtualBox, but I don't know it would work from there. I suppose I could load run a Windows 2000 start up disk off of a USB drive, but I don't see why I would need to do that in this day and age.

---

### Post by kerry_s on 2018-04-18
use the disks program. you can check filesystem or benchmark, etc....

---

### Post by Holger_Gehrke on 2018-04-18
SMART is the Self Monitoring And Reporting Technology built into most modern hard disks. If smartctl says the drive is incompatible this means it either doesn't have SMART (too old ?) or it's not in the programs database, which is used to interpret the data the drive reports (too new ?). Among the things SMART can report on are the cumulative run time of the drive, the number of power cycles, the number of unrecoverable read errors in the life time of the drive, and the number of bad sectors replaced from the reserve. Obviously the drive is nearing end of life if the reserve is used up and you're getting unrecoverable read errors.
While Linux can read and write NTFS and there are programs to create an NTFS in a partition, there are no programs for repairing damaged NT file systems on Linux (there is a program named ntfsfix, but that relies on marking the partition as 'needs chkdsk' and asking the user to boot into Windows for any but the simplest cases; it will find a lot of the possible problems but can't fix most of them itself). This is the reason why using NTFS on a Linux system without access to a system running Windows is not recommended.

Holger

---

### Post by oldfred on 2018-04-18
If NTFS you cannot run fsck on it. The fsck program is just for the ext2, ext3 & ext4 family of formats. There is dosfsck for FAT32, also.
The NTFXfix program really just turns on the chkdsk flag, so next time you boot Windows it will run chkdsk.

For NTFS you must use chkdsk from Windows or a Windows repair disk.
[https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc730714(v=ws.11)](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc730714(v=ws.11))

---

