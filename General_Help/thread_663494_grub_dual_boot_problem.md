---
title: "grub dual boot problem"
date: 2008-01-10
forum: General Help
---

### Post by go_beep_yourself on 2008-01-10
Whenever I try to boot Windows from Grub, I get the message "NTLDR is missing". If I do fixmbr from a Windows CD, won't that overwrite grub? How is this problem fixed?

---

### Post by kellemes on 2008-01-10
Try to search for a fix to be able to boot Windows again.. even if this means overwriting the bootloader.. Getting the bootloader back is a peace of cake using a liveCD or [SuperGrubDisk]("http://supergrub.forjamari.linex.org/").

Not sure if this helps..
[http://tinyempire.com/notes/ntldrismissing.htm]("http://tinyempire.com/notes/ntldrismissing.htm")

---

### Post by cbradley on 2008-01-10
hi

Search internet for supergrubdisk     download it put on cd or floppy and all your boot problems are over

---

### Post by matey3 on 2008-01-10
I would try to manually copy those windows file to the root of the boot drive (ie C:\) , I think there are 4 files like boot.ini ntldr ntdetect.com and ntbootdd
but my experience has been that sometimes when that  happens the folder called config under windows\system32 gets corrupted.(it contains the security stuff like passwd etc) but then again it may not be so try to copy over those 4 files. if they are there then edit your boot.ini file (bcs it seems that Grub is already doing its job)
good luck.

---

### Post by go_beep_yourself on 2008-01-10
> **cbradley said:**
> hi

Search internet for supergrubdisk     download it put on cd or floppy and all your boot problems are over

How could supergrubdisk fix it? Grub seems to be working fine, and I'd be able to reinstall grub from Linux.

---

### Post by logos34 on 2008-01-10
> **go_beep_yourself said:**
> How could supergrubdisk fix it? Grub seems to be working fine, and I'd be able to reinstall grub from Linux.

There's  a beta option under 'advanced>windows' in SGD to do the equivalent of **fixboot**.  It could be boot.ini is messed up.  Then again maybe the 'root' line in menu.lst windows entry is wrong, or perhaps the windows partition needs to run filesystem check (windows xp cd>repair console>**chkdsk /r**)

---

### Post by go_beep_yourself on 2008-01-10
Have you ever seen chkdsk do any good? I've ran it plenty of times, and it seemed to be useless. Windows still crashed constantly.

---

### Post by logos34 on 2008-01-10
did you run it with the repair option as above?  Personally, on my machine, on two occasions I've seen it find and correct bad sectors.  The rest of the time the disk was clean.  But you should always run it together with defrag before shrinking a windows volume.  (It will also run automatically afterwards upon reboot).  And it occasionally fixes windows booting problems.

---

### Post by go_beep_yourself on 2008-01-10
> **logos34 said:**
> did you run it with the repair option as above?  Personally, on my machine, on two occasions I've seen it find and correct bad sectors.  The rest of the time the disk was clean.  But you should always run it together with defrag before shrinking a windows volume.  (It will also run automatically afterwards upon reboot).  And it occasionally fixes windows booting problems.

I just ran it from the Windows installation disk. It didn't do any good. It took a long time to do. Yes, I ran it with /r repair option. Why does windows never work the way it's supposed to? I wish I didn't need it for gaming.

---

### Post by go_beep_yourself on 2008-01-10
> **matey3 said:**
> I would try to manually copy those windows file to the root of the boot drive (ie C:\) , I think there are 4 files like boot.ini ntldr ntdetect.com and ntbootdd
but my experience has been that sometimes when that  happens the folder called config under windows\system32 gets corrupted.(it contains the security stuff like passwd etc) but then again it may not be so try to copy over those 4 files. if they are there then edit your boot.ini file (bcs it seems that Grub is already doing its job)
good luck.

I need 64 bit files because I am using 64 bit Windows. I tried a ntldr from a 32 bit xp installation, and that did not help any. 64 bit xp is hard to find.

---

### Post by go_beep_yourself on 2008-01-10
> **logos34 said:**
> There's  a beta option under 'advanced>windows' in SGD to do the equivalent of **fixboot**.  It could be boot.ini is messed up.  Then again maybe the 'root' line in menu.lst windows entry is wrong, or perhaps the windows partition needs to run filesystem check (windows xp cd>repair console>**chkdsk /r**)

Super grub boot disk is too small to have a gui. Does it use a ncurses interface? If it gives me a command line only, then how can I do the fixboot thing? I don't believe the boot.ini line is messed up, but something in windows is messed up because it was working until it crashed. Then it wouldn't boot any more.

---

### Post by logos34 on 2008-01-10
To be more precise:

(Super Grub Disk menu)

English Super Grub Disk-->Advanced-->Windows (Advanced)-->Fix Boot of Windows (Partition).

---

### Post by mikewhatever on 2008-01-10
Can you post you menu.lst from Ubuntu.
> sudo cat /boot/grub/menu.lst

---

### Post by adrian15 on 2008-01-16
> **logos34 said:**
> There's  a beta option under 'advanced>windows' in SGD to do the equivalent of **fixboot**.

This option has been removed from new SGD versions due to possible copyright problems.

Do not ever try to find it! Do not waste your time.

adrian15

---

