---
title: "Booting problem"
date: 2020-06-21
forum: General Help
---

### Post by adedamolaxl on 2020-06-21
Hello, help me with this problem; my Acer 5xxxZ BIOS legacy laptop gives a loud noise after power on sometimes it also says no bootable device except if I hold the Fn key before powering on. The Linux seems to work fine if I log into it (it was there I ran boot repair which hasn't worked) but my Windows is incredibly slow. I suspect the booting problem has something to do with the Windows primary partition.  Pls help..

---

### Post by CelticWarrior on 2020-06-21
Welcome.

Please check your boot order in BIOS. Namely make sure it is set to the drive where Grub has been installed.
If you notice those settings changing or reverting then it's an hardware problem, the CMOS battery is dead.

Regarding Windows issues there are thousands of online resources for that.

---

### Post by adedamolaxl on 2020-06-21
Thank you Celtic. I think the boot order is right - HDD before ram before network. I have not noticed the boot order or any bios setting changing either. 

Do you have an idea of what could be happening to the Windows part of my system?

---

### Post by oldfred on 2020-06-21
Windows getting slow is a common problem. 
You may just need to do regular maintenance. 

One common probably is Windows NTFS gets very slow if it does not have enough room in the NTFS partition.
You typically need 30% free or unused. At 10% free you cannot do a defrag. 
You do regularly do a defrag & chkdsk? Not sure what else newer Windows needs.
My old XP took 5 min to boot, after defrag & chkdsk it was 'only' 3 min. Of course back then on same drive Ubuntu booted in 40 Sec.

---

### Post by GhX6GZMB on 2020-06-21
"Loud noise after power on" sounds to me like HDD mechanical failure. It happens more often than you think.

---

### Post by adedamolaxl on 2020-07-18
Just an update, windows has been working fine since then , there is still a loud noise tho but it's negated if I press the Fn key before power on

---

