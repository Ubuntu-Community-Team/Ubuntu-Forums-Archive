---
title: "System time"
date: 2005-10-26
forum: General Help
---

### Post by jimmy41 on 2005-10-26
I have a dual boot (xp and ubuntu).  The problem I have is with my XP boot.  

After I boot to Ubuntu and then boot back to XP, my system time in XP is several hours ahead.  When I boot back to Ubuntu its fine, even if I change the time ahead in XP.

This a known issue?

Thanks

---

### Post by dhjohnson on 2005-10-26
I believe the situation is caused by Ubuntu setting the system/BIOS clock to GMT/UTC--a standard linux/unix practice.  It then adjusts the software clock (e.g. the system tray) to your local timezone.  Windows, on the other hand, just uses the system/BIOS time--no adjustment is made, so the time Windows gives is GMT/UTC.

Unfortunately I don't know how to get Ubuntu to leave the system clock set to a local timezone, or to get Windows to get that the system clock time is GMT/UTC.  A slightly less elegant solution might be to adjust the Windows timezone to GMT/UTC.

---

### Post by PriceChild on 2005-10-26
I believe that during the setup it asks you whether to enable this option or not.

I doubt you'll be wanting to re-install at all :P But just decided i'd slip this in :)

---

### Post by tb525 on 2005-10-27
This works: [http://www.majalah.com/#disablesystemtimedateutc](http://www.majalah.com/#disablesystemtimedateutc)

   1. sudo cp /etc/default/rcS /etc/default/rcS_backup

   2. sudo gedit /etc/default/rcS

   3. Find this line:
UTC=yes
   4. Replace with the following line:
UTC=no

   5. Save the edited file 
   6. System -> Administration -> Time and Date
Set the correct time/date

   7. sudo /etc/init.d/hwclock.sh restart

---

