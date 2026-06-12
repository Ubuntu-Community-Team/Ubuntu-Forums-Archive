---
title: "The clock in XP is 2 hours off after Ubuntu installation."
date: 2005-10-23
forum: General Help
---

### Post by Smirf on 2005-10-23
I have Ubuntu 5.10 and XP in dualboot on my computer. After every time I boot XP to play games etc the time is 2 hours behind in Windows. I have the same timezone in Linux and Windows. I did not have this problem before I installed Ubunutu.

Does anyone know how to fix this problem?

---

### Post by moffa on 2005-10-23
The problem is that Linux generally sets your time to UTC (GMT) where as windows sets your time to local.  To configure Linux to keep your time to local time you need to change the settings below:

From Ubuntuguide.org:

How to disable system time/date from being reset to UTC (GMT)?

sudo cp /etc/default/rcS /etc/default/rcS_backup
sudo gedit /etc/default/rcS

   3. Find this line

...
UTC=yes
...

   4. Replace with the following line

UTC=no

   5. Save the edited file (sample)
   6. System -> Administration -> Time and Date

Set the correct time/date

   7.

sudo /etc/init.d/hwclock.sh restart

---

### Post by XDevHald on 2005-10-23
[quote=Smirf]I have Ubuntu 5.10 and XP in dualboot on my computer. After every time I boot XP to play games etc the time is 2 hours behind in Windows. I have the same timezone in Linux and Windows. I did not have this problem before I installed Ubunutu.[/quote]

**EDIT: **Check the above post from this one, it seems to have a better layout on how to help your settings error :)

---

### Post by clparker on 2005-10-23
Problem is microsoft. Basically, linux and windows dont see eye to eye on how to set the time, it's windows seeing the linux entry in the hardware clock and not reading it right. Personally I blame microsoft. , i dont use microsoft.

---

### Post by Smirf on 2005-10-23
Moffa: I did what you wrote. The time is correct now :)

Thanx for the help.

---

