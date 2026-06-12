---
title: "How to Repair MBR for XP?"
date: 2008-03-01
forum: General Help
---

### Post by Papa.Gario on 2008-03-01
How do I repair the windows XP MBR?

I get the "a disk read error has occurred, press ctr alt del to continue" when I try to boot windows.  

I don't have a windows cd. (fixmbr)

I have gparted and super grub cd, but neither of those work.


Any Ideas?

---

### Post by oilchangeguy on 2008-03-01
Go to [www.bootdisk.com](www.bootdisk.com) from there you can create an xp boot cd. I've never used this site, so can't tell you if it will work. But with a standard xp install disc, (not a factory restore cd) once it loads you'll be presented with several options, select R to enter the repair console. Select the version of windows you want to repair (usually only one choice), enter the admin. password, if there's not one just press enter. At the command prompt type, fixmbr and press enter. Then type fixboot and press enter. Then type exit. And reboot the computer.

---

### Post by rapiscan on 2008-03-01
There are a couple of suggestions on this thread, regarding how to fix the mbr without a cd.

[http://ubuntuforums.org/showthread.php?t=391387](http://ubuntuforums.org/showthread.php?t=391387)

---

