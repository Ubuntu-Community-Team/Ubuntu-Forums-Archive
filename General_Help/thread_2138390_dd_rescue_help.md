---
title: "dd rescue help"
date: 2013-04-23
forum: General Help
---

### Post by des1 on 2013-04-23
I have a WD 2tb hdd which recently failed, it makes a clicking noise but
still spins. It is found in the bios, device manager and in linux but I cant
mount the disk and it gives 49 currently unreadable sectors. I tried dd
rescue onto my 3tb ntfs hdd with the following command  ddrescue -f -d -r3
/dev/xxx /dev/yyy /path/to/logfile it starts up but nothing transfers it
gets 1 error and this error goes up to a size of 2tb?? then tries Trimming
but this also this is to no avail. Is this hdd declared dead? Should i now
try the freezer trick? Any help would be appreciated.
--

---

### Post by cbraxton on 2013-04-23
The "freezer trick" is an absolute last resort that in my experience rarely works. (I have seen it work occasionally, maybe about 5% of the time.)

If you have no intention of sending the drive to a professional data recovery lab you have nothing to lose, might as well try it. However, if the information on the drive is sufficiently valuable that you're considering using a lab then you don't want to freeze the drive as that may well do more damage, hampering further attempts at recovery.

---

