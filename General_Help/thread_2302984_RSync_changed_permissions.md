---
title: "RSync changed permissions"
date: 2015-11-15
forum: General Help
---

### Post by FreakShow! on 2015-11-15
Hi,

I've got two external hard drives and use them as backup drives. Normally there's not a huge difference between the two so I just plug them both into my Windows machine and copy the files over.

This time though, there was a lot of changes so I figured I'd do something a little more clever and used RSync to synchronise the two. That seemed to go well and after many hours it was done in the one direction.

However, the drive that received all the changes is now really being a pain. In Windows it'll sometimes pop up as showing as a RAW drive. Sometimes it'll show up, but only the root folders are present and each is empty. Sometimes Windows will say it doesn't recognise the drive. If I plug it into a Linux machine, the files are all there as expected.

I've already run ntfsfix but am guessing that something with permissions has gone very wrong. Is there anything I can do to sort it out? Or am I just going to have to copy the contents off on a Linux machine and clean erase it?

I don't believe the drive is faulty at all, because it works under Linux, so it must be a software level issue.

Thanks.

---

### Post by oldfred on 2015-11-15
Not rsync, but NTFS format.

Windows formats have no owership nor permissions, so you cannot preserve them when copying files from Linux to NTFS. If just your data files, not a big issue as you can easily reset when you restore to /home or your data partition. But if system files, it is like having no backup at all. But with Linux it is easy to reinstall system, but you may lose your customization.

Linux fixes to NTFS formats do not do much. ntfsfix only sets the chkdsk flag. You probably need to run full chkdsk from Windows on your NTFS partition(s).

---

### Post by SeijiSensei on 2015-11-15
NTFS also doesn't support things like symlinks.  If I have to back up to an NTFS-formatted drive, I'd rather tar the directories first, then transfer the entire .tar.gz file to the NTFS device.

---

### Post by FreakShow! on 2015-11-15
Well I'm doing a checkdisk now on Windows. I think in future I'll try and avoid using Linux and NTFS then. 

It's a shame that there isn't a filesystem that is compatible with all 3 OS' (Win, Lin, OSX) but doesn't have any limitations like FAT32 does.

---

