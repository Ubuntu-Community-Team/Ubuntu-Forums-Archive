---
title: "How to make the brightness setting persistent in ubuntu 12.04.2?"
date: 2013-03-27
forum: General Help
---

### Post by chk1827 on 2013-03-27
When i was using ubuntu 11.04, this was not a problem..whichever brighness setting i used to set was persistant after rebooting...
but in 12.04 every time the system restarts the brightness setting is reset to minimum...
What is the problem and is there any solution for it??:confused:
 
I tried editing /etc/default/grub file and changed GRUB_CMDLINE_LINUX="quiet splash" to 
GRUB_CMDLINE_LINUX="quiet splash acpi_osi=Linux acpi_backlight=vendor"
but that did'nt work for me..the brightness bar did'nt work..brightness was constant and would not be changed with the brightness bar..so i changed it back to "quiet splash"

Now i am thinking of a workaround using the script method, ie., 
sudo gedit /etc/rc.local
echo 4 > /sys/class/backlight/acpi_video0/brightness

but i want to do this only if there's no proper solution for this bug..

my VGA controller is(lspci | grep VGA)
VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

Any help would be appreciated :popcorn:

---

### Post by chk1827 on 2013-03-27
Tried editing the /etc/rc.local file but that did'nt work either..

---

### Post by CaptainMark on 2013-03-27
I have the same problem, I tried to find out before but could not find an answer back when I tried, it was an un-resolved bug. Hopefully that has changed but searching the web is still bringing nothing useful.

---

