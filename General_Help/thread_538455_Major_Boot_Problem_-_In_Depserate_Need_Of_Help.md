---
title: "Major Boot Problem - In Depserate Need Of Help"
date: 2007-08-30
forum: General Help
---

### Post by GallienKreuger on 2007-08-30
Hi all, any help you can lend me would be greatly appreciated.

I've never used Linux before and was very interested in trying it out, so I installed Wubi on my system.  I have an HP Laptop that runs the Media Center edition of Windows XP.  For whatever reason, after I had played with Ubuntu in Wubi a few times with a few normal reboots after upgrades, I rebooted and now the my computer won't boot any operating system.  It defaults to Windows XP, says it won't boot correctly, I go to safe mode, and then a blue screen flickers and the system restarts.  I could really use some help as this is my main computer system.

Again, please help, as you can tell, I'm very confused and severely panicked.

Thanks,
Dan

---

### Post by tuxcantfly on 2007-08-30
Ouch, sounds like filesystem corruption

boot up a windows xp recovery cd

press "r" for recovery mode

enter "chkdsk /r" and wait as it checks and fixes your filesystem, hopefully it'll boot after that

---

### Post by GallienKreuger on 2007-08-30
My system came with XP preloaded and no boot disk (also doesn't have a floppy drive).  Do you know what files (and where to find them on an xp computer of the internet) to compile onto a CD to use that as a boot disk?

---

### Post by hh93 on 2007-08-30
> **GallienKreuger said:**
> My system came with XP preloaded and no boot disk (also doesn't have a floppy drive).  Do you know what files (and where to find them on an xp computer of the internet) to compile onto a CD to use that as a boot disk?

you need BartPE ([http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/))

---

### Post by clive_pearce on 2007-08-30
BartPE has not been updated for sometime. 

Get ubcd4win [http://www.ubcd4win.com/](http://www.ubcd4win.com/)

This has an option to boot to the recovery console. It is based on BartPE.

Or borrow an XP disk.

---

### Post by hh93 on 2007-08-30
agree

---

