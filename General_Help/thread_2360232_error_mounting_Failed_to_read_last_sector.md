---
title: "error mounting: Failed to read last sector"
date: 2017-05-02
forum: General Help
---

### Post by ubeu on 2017-05-02
First of all, I wonder whether this is the most appropriate forum for this question. Please excuse if there is more appropriate (sub)forum. I should also mention that my knowledge of both linux and filesystems is beginner's level.

I have this external hard drive that is corrupted to some extend. Testdisk was able to restore the ntfs filesystem, but while the hdd's size it 4TB, the number of sectors is much higher (disk end after the disk's physical end). At the same time, Gparted does detect the correct size of the hdd (see attached screenshot).

Ubuntu and gparted display the same error message: Failed to mount:
[INDENT]   "Failed to read last sector (976558590): Invalid argument

 HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,

    or it was not setup correctly (e.g. by not using mdadm --build ...),

    or a wrong device is tried to be mounted,

    or the partition table is corrupt (partition is smaller than NTFS),

    or the NTFS boot sector is corrupt (NTFS size is not valid).

 Failed to mount '/dev/sdc1': Invalid argument

 The device '/dev/sdc1' doesn't have a valid NTFS.
 Maybe you selected the wrong device? Or the whole disk instead of a

 partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?"

 
 
[/INDENT]

I already ran photorec, resulting in the recovery of files without their original names or folder structure.
Now I would like to restore/access the original filesystem, folders and files. 

Does anybody have advice on how to try to accomplish this?
Thank you

---

### Post by yancek on 2017-05-02
Per the message you posted, do you or did you have RAID configured on this drive?

If the corrupted filesystem on the partition in question is the proprietary windows ntfs, I doubt you will have much luck repairing it with Linux tools and you would be better off using some windows tools.  You could try your windows repair or installation DVd.

---

