---
title: "Windows scan disk from linux?"
date: 2007-01-01
forum: General Help
---

### Post by DMAthlon on 2007-01-01
I'm having problems booting into my windows XP and i want to try a sacn disk so can anyonehelp me out and tell me if i can do a scan disk on an NTFS partition from LInux?

---

### Post by Qchan on 2007-01-01
[b][color=darkred]
You can't do a chkdsk (fsck) scan on an NTFS partition on Linux. Not unless you're using so sort of emulation tool. You're better off finding tools to boot into the Recovery Console for Windows and running chkdsk /r

[/b][/color]

---

### Post by DMAthlon on 2007-01-01
are there any linux apps for doing it on an NTFS, cuz linux reads all the data on my NTFS partitions fine.

---

### Post by houstonbofh on 2007-01-02
> **DMAthlon said:**
> are there any linux apps for doing it on an NTFS, cuz linux reads all the data on my NTFS partitions fine.
If you are using the ntfs-3g, there are some utilities there.  [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by Dies on 2007-01-02
> **Qchan said:**
> [b][color=darkred]
You can't do a chkdsk (fsck) scan on an NTFS partition on Linux. Not unless you're using so sort of emulation tool. You're better off finding tools to boot into the Recovery Console for Windows and running chkdsk /r

[/b][/color]

I'm pretty sure you can do this with gparted and ntfsprogs.

---

### Post by QuinnHarris on 2007-01-02
Linux does not have a full NTFS file system checker but it does have 'ntfsfix' which will cause windows to check the file system when it boots.

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/hda1

replace hda1 with the appropriate device, use 'cat /proc/partitions' for a list

Problems with windows booting could be indicative of a hard drive problem.  I would recommend running a hard drive self test.  The following will use the hard drives built in test facility.  If this test fails I would replace the drive.  Hard drives don't typically outright fail, but when they start having problems, usually more problems are to come.

sudo apt-get install smartmontools
sudo smartctl -t long /dev/hda

then

sudo smartctl -a /dev/hda

This will dump alot of output about the drive and tell the progress of the self test.

---

