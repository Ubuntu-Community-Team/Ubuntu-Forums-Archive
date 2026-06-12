---
title: "Slow rysn backup"
date: 2013-01-03
forum: General Help
---

### Post by vaaaaal on 2013-01-03
I am trying to perform a backup from my computer to an external hard disk using the command:

rsync -avvhu --max-size='3G' $DRIVEPATH $MACPATH

When I run this command *some* *files* that have not been touched since the last backup still seem to get copied while others are left alone. Here is are a few lines of output from the third run within a period of several minutes:
Resources/Polarization/Polarimeters/Ramaprakash_single_ccd_wollaston_prism.pdf is newer
Resources/Polarization/Polarimeters/WilliamSparks_Spectropolarimetery.pdf is newer
Resources/Polarization/State_Polarization_Code/._StatePol.pdf is uptodate
Resources/Polarization/State_Polarization_Code/StatePol.m is newer
Resources/Polarization/State_Polarization_Code/StatePol.pdf is uptodate

Does anyone know why rysnc is saying these files are "newer" when they are not? The total sent from the summary at the end does confirm that they are being copied over.

---

### Post by vasa1 on 2013-01-03
I'm pretty new to rsync but [papibe pointed out]("http://ubuntuforums.org/showpost.php?p=11283151&postcount=2") that syncing to different formats could produce a time difference artifact:> When re syncing your files to the external disk, you may encounter a situation in which all files are copied again, even though they hasn't been modified. This is because ntfs handles the modification times a little more relax.

To deal with this add the option --modify-window=1 to adapt to ntfs' system.

I don't know if that applies to your case but just in case!

---

### Post by SeijiSensei on 2013-01-03
Does the backup target use a POSIX filesystem like ext4 or ext3?  Backing up to NTFS is often problematic because of the absence of compatible permissions, timestamps, and other filesystem primitives.  If the backup device needs to support both Windows and Linux, I'd considered partitioning it into two parts and formatting one with NTFS and the other with ext4.  Then backup the Linux machines to the ext4 partition and the Windows machines to the NTFS one.

If you're only backing up Linux machines, wipe the target drive and reformat it as ext4.  You'll solve all your problems then.

---

### Post by vasa1 on 2013-01-03
On reflection, OP has the problem only with **some** files. How can that be explained?

---

### Post by vaaaaal on 2013-01-03
You guys hit the nail on the head, the external drive is NTFS. I actually have to be able to access the same data from a Mac and a PC so I need to keep it NTFS. I'm not sure why it was only happening to some files but fortunately vasa1's suggestion to use the option --modify-window=1 worked perfectly.

Thanks for your help!

---

### Post by vasa1 on 2013-01-03
> **SeijiSensei said:**
> ...  Backing up to NTFS is often problematic because of the absence of compatible permissions, timestamps, and other filesystem primitives.  ...
Hi, could you please explain in somewhat simpler terms for users who are *not* sys admins and are *not* looking after multi-user computers or networks, etc. Why would NTFS be an issue for those who just want to back up their data differentially and who would be essentially concerned with whether a file has been updated or not?

---

### Post by vaaaaal on 2013-01-16
Setting the modify window equal to 1 helped a lot but I am still having a bit of trouble. On one hard drive this solved all of my problems. Unfortunately I have a second hard drive (formatted the same) for which this fix only worked for files, *every *directory is still backed up *every time* I run rsync. I am trying to back up the entire file system so this actually adds quite a bit of time. Any ideas as to what might cause this?

I looked again and I actually have been using FAT32 not NTFS if that makes a difference to anyone.

---

### Post by vaaaaal on 2013-01-16
Reformatted the disk (still as FAT32) and the problem seems to be gone. It all seems very mysterious. My problem is technically solved but I'm still curious if anyone has any insight here.

---

