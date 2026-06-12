---
title: "can't get back to windows XP, stuck on grub rescue prompt"
date: 2012-12-30
forum: General Help
---

### Post by Chaimon on 2012-12-30
I have been running ubuntu 11 on a Toshiba laptop alongside windows XP. I (stupidly) DELETED the drive with ubuntu on it (in effort to uninstall ubuntu) and tried to combine the "unallocated" space to the c: drive for XP (did this while running XP). After restarting computer, I only get this:

ERROR: NO SUCH PARTITION.
GRUB RESCUE>_

Yes, little grub, I deleted that partition!!! Oops. 

What I want is to boot into windows from the c: drive. But how? 

I tried putting the original installation disc in the drive and rebooting, but no luck (computer does not "see" the disk. Has anyone had and resolved this problem?

More background info: I started out just trying to uninstall ubuntu, but it did not appear in any list of installed software. I read somewhere in these forums to delete the partition and that that would essentially do the job. Any ideas?

---

### Post by xc3RnbFO8P on 2012-12-30
You can install Ubuntu again
or try Boot repair.....
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by Chaimon on 2013-01-05
Thanks for reply. But I can't install anything, because the computer boots directly to the grub rescue prompt. I don't know grub commands, and can't find them online.

I tried the boot repair disk, but of course it had no effect (computer isn't reading the disk drive).

---

### Post by xc3RnbFO8P on 2013-01-05
> **Chaimon said:**
> Thanks for reply. But I can't install anything, because the computer boots directly to the grub rescue prompt. I don't know grub commands, and can't find them online.

I tried the boot repair disk, but of course it had no effect (computer isn't reading the disk drive).

can you not run Ubuntu from a live disk?

---

### Post by Chaimon on 2013-01-05
No. I tried inserting the original ubuntu 11 disk (an .iso) and got nothing. Computer goes immediately to "grub rescue" prompt with error "no such partition".

Also -- what I find online says that to use a live disk you must "configure your computer to boot from the drive." I can't do that.

---

### Post by xc3RnbFO8P on 2013-01-06
and you tried these option 
> ESC, F1, F2, F10, Ctrl-Del or Del
when you get blinking cursor?
F10 should work on newer computer.

---

### Post by Chaimon on 2013-01-06
> **Ringi said:**
> and you tried these option 

when you get blinking cursor?
F10 should work on newer computer.

Okay, I tried these options, but nothing happened at all. Yes, the cursor is blinking.

---

### Post by xc3RnbFO8P on 2013-01-07
Check this:
[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

