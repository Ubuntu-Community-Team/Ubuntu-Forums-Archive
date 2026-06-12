---
title: "Wubi 7.10 windows repeating boot"
date: 2008-01-17
forum: General Help
---

### Post by almightybacon on 2008-01-17
Hi, I installed wubi 7.10 from the developer minefield because it was supposed to be safe and easy ;)

Everything worked fine for days, but then i installed ubuntustudio.
the rt kernel is pretty damned flaky, and i was unable to shutdown properly, so unfortunately the system experienced a hard shutdown.

now, ubuntu works just fine.  I have read/write access to the windows filesystem, but i cannot boot into windows. it just reboots after it starts.

i suspect this is due to a corrupted NTFS filesystem.
already ran chkdsk /p which found errors and then chkdsk /r which allegedly "repaired it", but no luck.

Perhaps some windows files are corrupted.  is there any easy way to identify which ones and perhaps manually replace them from a system that is known to be working?   ... or am i way off track here.

of course the easy answer would be to simply re-install windows.  but i'd really rather not do that.

any ideas?

---

### Post by almightybacon on 2008-01-17
when looking at the root directory of c: drive (mounted at /media/windows)
i noticed a couple alarming things.
disclaimer: i'm no windows expert but this stuff seems fishy to me.

the files autoexec.bat, config.sys, io.sys, and msdos.sys all appear to be empty and blank. this is not what i'm normally used to.  but i've never had to maintain xp on that level.

what could have caused this?

additionaly in the same directory is the file booetx.log which appears to be a log of my attempt to do the old chkdsk /r    in this file is a few thousand entries that look something like this:

Deleting an index entry from index $O of file 25.

The object id index entry in file 0x19 points to file 0x910

but the file has no object id in it.

i doubt this means anything but the condition of the autoexec.bat as well as other files is alarming.

can i simply replace or reconstruct those files? does it need to be done? does XP even actually use any of that stuff anymore?

any help would be very much appreciated.

**edit** 
ok well i guess windows doesn't actually use those files anymore so i suppose it makes sense that they are blank.

---

### Post by Ocxic on 2008-01-17
try putting in your XP CD as you go through the install procedure, it wil present an option to repair the installation, try that..

be advised you may have to re-install grub afterwards.

---

### Post by almightybacon on 2008-01-17
yes, i tried that, and ran chkdsk /r from the recovery console,  additionally i also tried fixboot as well as replacing the master boot record.

what's left to do?

is windoze broken beyond repair?

---

