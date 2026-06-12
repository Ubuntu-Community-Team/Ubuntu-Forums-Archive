---
title: "Does Ubuntu Live create any temporary files?"
date: 2005-05-25
forum: General Help
---

### Post by obonto on 2005-05-25
Hello,

does the Ubuntu Live CD for PPC create any temporary files or other stuff (swap files) on my harddisk?
If yes, does it delete these files after shutting down?

obonto

---

### Post by the_clown on 2005-05-25
[QUOTE=obonto]Hello,

does the Ubuntu Live CD for PPC create any temporary files or other stuff (swap files) on my harddisk?
If yes, does it delete these files after shutting down?

obonto[/QUOTE]
 All the settings are saved to the RAM, nothing is saved on the harddisk.

---

### Post by jdong on 2005-05-25
No, it doesn't touch the hard disks at all, with one exception:


If it detects a Linux Swap Partition (type 0x82) on your system, with a valid swap signature (meaning you aren't hibernated or otherwise storing important stuff on the swap partition), Ubuntu LiveCD **WILL use it.** This is usually beneficial, not harmful.

---

### Post by sooqing on 2005-08-03
Ubuntu just broke off my relationship with my partner. I promised him that Ubuntu Live 5.04 won't touch the HDD at all.. same as all the other Linux Live CDs I had tried.. so I tried to boot off the CD and when the system hanged halfway, I performed a cold reboot of the PC.. the entire HDD became unreadable and I had to reinstall XP for him.. and ending our relationship at the same time..  :(

---

### Post by pszilard on 2005-08-06
[QUOTE=sooqing]Ubuntu just broke off my relationship with my partner. I promised him that Ubuntu Live 5.04 won't touch the HDD at all.. same as all the other Linux Live CDs I had tried.. so I tried to boot off the CD and when the system hanged halfway, I performed a cold reboot of the PC.. the entire HDD became unreadable and I had to reinstall XP for him.. and ending our relationship at the same time..  :([/QUOTE]
 This scary! I am married and can't afford a divorce :) -- actually the wife wouldn't touch a PC without me holding her hand!

But it is still scary as I was thinking of using Ubuntu Live CD on my works laptops. Maybe I should stick to Knoppix?

-paul

ps: I tried the Live DVD. It didn't touch my XP installation, just didn't work. The screen went blank at the end of the boot, even though O specified the resolution on the Dell Inspiron 6000.

---

