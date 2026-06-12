---
title: "USB hdd spindown"
date: 2006-07-11
forum: General Help
---

### Post by MatBi on 2006-07-11
Hi,
i have an external USB 2.5" hdd that never spins down, even if not mounted.
I tried to connect it via ATA interface and set the power management/sleep parameters and reconnect it via USB, but it didn't work.
How can i spin it down via USB? 
Thanks in advance,
MatB

---

### Post by newbieforever on 2008-03-17
same problem! help!
i can't enable laptop-mode, because that would disable (remove, actually) ubuntu desktop (a bit drastic, inst it?)

if i try get the following

~$ hdparm -C /dev/sda
/dev/sda:
 drive state is:  unknown

~$ hdparm -S 120 /dev/sda
/dev/sda:
 setting standby to 120 (10 minutes)
 HDIO_DRIVE_CMD(setidle1) failed: Invalid argument
~$ 

thanks in advance

newbie forever
___________________

update:
i found out that:
desktop hdd are designed about 50,000 spinups
laptop and in general 2.5" hdd (as most of usb hdd) are designed about up to 300,000 spinups
on statistic base, i mean... hardware failure excluded
i install every os only on external usb drives, because in case of failure i have no problems about restore data ("/home" partition mount point or "documents and settings") and transfer my system image to another disk
so, a good 2.5" hdd (i mean western digital, maxtor<-->seagate, hitachi) shouldnt need frequently spindowns, if you dont have power consumption issue
i almost always use computer (laptops i mean, desktops dont exist for me) on ac power, unless i have to move them from a room to another
the battery is for me a sort of ups-like integrated system
and i dont care about battery health 
(in fact it reduced its power-supply time at 50% of the beginning, 2 years ago)
that's all, so i really dont need to spindown my drive
the advantage is a more responsive system, obviously

what do you think about that?

thanks again

nbfe

---

