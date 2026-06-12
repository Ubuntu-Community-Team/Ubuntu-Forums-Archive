---
title: "Hard drive erased?"
date: 2007-06-28
forum: General Help
---

### Post by azizzle on 2007-06-28
I was dual booting xp and ubuntu... and then decided to just run ubuntu on my laptop. so i ran partition magic on my desktop to erase the linux partitions and thought everything was all good. then when i rebooted it grub came up with an error 22. so i was like shoot, i guess i'll just have to dual boot till i find out how to get rid of or bypass grub. so i go to reinstall ubuntu and when it comes to resizing the drive it freezes. so i reset the pc and try over and now linux isn't recognizing the windows that was on there before. right now when it asks how to partition the disk it says 
guided-use entire disk
when before there was a meter that i could define the size i wanted.
so 
1.did my hd get wiped out when i reset my computer? 
2.is there a way to bypass grub from bios?
-

---

### Post by kidders on 2007-06-30
Hi there,

> **azizzle said:**
> so i go to reinstall ubuntu and when it comes to resizing the drive it freezes.Why did you opt to resize your disk partitions? Presumably, partition magic left you with plenty of unallocated space to install Linux into.

> **azizzle said:**
> 1.did my hd get wiped out when i reset my computer?It's hard to know. If I were you, I'd try to investigate the damage with some forensic data recovery apps, and perhaps take a disk dump as a backup, just in case I needed it.

> **azizzle said:**
>  2.is there a way to bypass grub from bios?You can simply overwrite a bootloader to kill it. To bypass grub using your BIOS (ie keep it but stop using it), you'd have to have two or more hard disks.

---

### Post by bren on 2007-06-30
try this system rescue livecd
maybe partition table is corrupted in which case testdisk will fix it

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

bren

---

