---
title: "CloneZilla of disk with mutliple operating systems question ..."
date: 2018-08-17
forum: General Help
---

### Post by michael351 on 2018-08-17
I have an Acer PC with both Windows 10 and Ubuntu 16.04 installed.
I am preparing to upgrade Ubuntu to 18.04 and before I do that I want to backup my Ubuntu 16.04 using Clonezilla.

This is the first time I will be using Clonezilla.

Any suggestions on how to use Clonezilla to backup my system? Should I just back up the Ubuntu 16.04 partition? or do a full disc image somehow? (will that backup the MBR and windows 10 system as well?).

Looking for any suggestions on what you would do in my situation. Thanks.

(p.s. I haven't backed up in the past since I would just re-install if my disk crashed - but now my system has much more user data and applications that make backing up smart to do at this stage. I don't want to upgrade to Ubuntu 18.04 until I get the old system "cloned" and saved).

---

### Post by VMC on 2018-08-17
Here is some screenshots and a guide to follow. It can be a bit confusing on first time through. Backing up ubuntu partition will auto backup mbr. No need to backup windows, but you can do both.
[https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image](https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image)

edit: I prefer *fsarchiver* when backing up linux partitions.

---

### Post by TheFu on 2018-08-17
I would buy a new HDD/SSD, and use that for the new install. No need for a backup, if you aren't already making them.  Of course, **you should be making a backup at least weekly.**

If you copy the entire disk device (/dev/sda) then you get the partition tables, UUIDs, partitions, file systems, and all bits inside the files. If the target disk isn't the identical size with the same sector sizing, this method has problems.

If you copy at the partition level (/dev/sda1), then you get the file systems (or LVM + file systems), and all the bits inside the files. At restore time, you'll need to manually create partitions as required.  This can be helped by using fsarchiver instead of clonezilla/dd/ddrescue/partimage.

For most typical, non-technical, end users, using a tool like **Aptik** to make backups is the easy/sufficient answer.  There really isn't much need to backup 5G of the OS stuff.  What you need are your files, your settings, some system settings, and list of installed programs. 
To restore, use the 16.04 ISO, do a fresh install, then manually install aptik and restore the aptik backup stuff, including the previously installed packages.  All good. Fairly painless.  Definitely worth practicing BEFORE you need it.  Doing it this way should take less than 45 minutes to have a desktop that feels just like the prior one with most of your data restored.  Only the large media files might make that time longer.  I keep media elsewhere to avoid that delay in the restore process.

Make sense?

---

### Post by oldfred on 2018-08-17
Is system UEFI or BIOS?

If UEFI, then you have gpt partitioning and really need to only use full drive imaging. Or just copy your data as TheFu suggests. 
Gpt has partition GUIDs in the primary partition table, the partition and the backup partition table. And various checks that data is in sync.  So copying a partition usually gets GUIDs out of sync. May be fixable with gdisk but better not to have issue.
Full drive clone then includes all the partition data.

If BIOS/MBR then you can copy individual partitions.

---

### Post by michael351 on 2018-08-18
System is BIOS. I am looking at Aptik to backup the system, then I will install 18.04 as per the advice above.
Thanks everyone.

---

