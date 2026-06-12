---
title: "Ubuntu 12.04/Windows 8 dual boot - time wrong at startup"
date: 2014-03-20
forum: General Help
---

### Post by LifeEnemy on 2014-03-20
Hi all,

I have an Acer Aspire V5-572g with ubuntu and Windows 8.1 set up with a dual boot. The OSes are on a 128gb SSD card I added, and I have a 500gb HDD split into NTFS and Ext4 partitions for storage. I've been having a problem that I thought was isolated to Windows (and I've been trying to get help on that with little success), but I now find may be more basic.

My problem is thus: when booting the computer, the time displayed is incorrect, though the correct time zone is selected. It doesn't happen every time I boot, and seems to happen more often when my computer has been off for some time, rather than when I restart it. I just noticed this morning that it happened in Ubuntu as well as Windows. The problem is solved by forcing the time to sync with the internet (on Windows). On Ubuntu I turned the clock off and on, as there isn't an obvious button to sync with internet time. However, this is a frustrating process to have to go through every time I start my computer. The time always seems be to be about 17 hours ahead of the correct time, and as far as I can tell it's been very consistent on that front.

I've checked the time in BIOS and it is correct. I've read with issues about a dying battery, but I don't think that's the case as this computer is only a few months old and the time is always off by the same amount. The fact that it's happening in both OSes makes me this the dual-boot is somehow involved.

I'm not sure if it's relevant, but whenever I shut down Windows I get an error message on a BSOD saying there was a problem and windows must restart. That happens almost every time, so I have to restart into Ubuntu in order to actually shut down my computer. I've seen "Unexpected_kernel_mode_trap" and "System_service_exception" error messages, and maybe others.

What could be causing this issue with my computer's timekeeping, and how can I fix it??

Thank you.

---

### Post by Impavidus on 2014-03-20
First thought is a mixup between local time and Greenwich time, although 17 hours is a bit much – or is it really 7 hours in the other direction? The common problem is that Windows sets the BIOS clock to local time, where Linux prefers it in GMT. So is the BIOS clock correct in local or Greenwich time?

There is a setting that makes Linux interpret the BIOS time as local time instead of GMT. Open the file /etc/default/rcS and change, if necessary, UTC=yes to UTC=no. You'll need root permissions for editing this file.

---

### Post by mrcameronnewton on 2014-03-20
Is the BIOS Time Correct?

Check your BIOS Settings (Most bios'es have a Graphical User Interface that you can Change the time)
Ubuntu checks the Time of the BIOS sometimes and Auto-Updates it Ignoring your Timezone Settings
Sometimes the Bios can take ages to Update Ubuntu's time so Maybe Restarting the Time Service or Unity might fix the problem

---

### Post by LifeEnemy on 2014-03-20
It was definitely 17 hours into the future, based on the date. Though now I'm not sure. Ubuntu I think was at -7 hours. I'm in GMT-8 though, so that's odd.

It seems as though Ubuntu was changing the BIOS time to match GMT, so that's part of the problem. I changed the rcS file so it reads it as local time now. The math with the Windows time doesn't add up, but this might've solved the problem.

I'll post back if it resurfaces. Thank you!

---

