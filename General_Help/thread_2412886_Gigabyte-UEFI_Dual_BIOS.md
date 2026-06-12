---
title: "Gigabyte-UEFI Dual BIOS"
date: 2019-02-18
forum: General Help
---

### Post by SUPERFITTER on 2019-02-18
I am running Ubuntu 16.04 on a dual boot with Windows 7.  When I boot the computer I get this message (see below).  I have tried the first two and get the same problem when I boot.  I would like to go into BIOS and find a fix to this problem, BIOs has been reset-please decide how to continue,  but I do not know where to start?

Thank You
Dennis

[FONT=times new roman]**Gigabyte-UEFI Dual BIOS**
[/FONT]
[FONT=times new roman]BIOs has been reset-please decide how to continue
[/FONT]
[FONT=times new roman]Load Optimized defaults then boot[/FONT]

[FONT=times new roman]Load optimized defaults then reboot[/FONT][FONT=times new roman]
[/FONT]
Enter BIOS

---

### Post by oldfred on 2019-02-18
After updating UEFI/BIOS, you generally have to go back into UEFI to redo the changes you made.
It normally resets to "optimized" defaults which probably is Secure Boot on and other settings.
I have to keep a list of changes I make so I can easily redo them.

Are installs UEFI or BIOS. If BIOS, then you must have Secure Boot off. And Windows 7 in UEFI boot mode does not support Secure Boot. Often systems say "Windows" or "Other" but fine print in manual says if booting Windows 7 you must use "Other".

What model motherboard?
What video?

---

### Post by rbmorse on 2019-02-18
Another thing to check iIf it's an older computer: the battery that maintains settings in the CMOS memory on the motherboard may require replacement.

---

### Post by SUPERFITTER on 2019-02-18
I did not update BIOS, BIOS [FONT=times new roman]has been reset on its own?  [/FONT]

---

### Post by oldfred on 2019-02-18
Linux now has tools to update some UEFI, but Gigabyte is not yet on the list.
I do not think Windows does either, for motherboards. If Gigabyte system it may update UEFI.

If you went into UEFI and clicked the revert to defaults or optimized settings then the settings are changed, but UEFI is not updated. You still need to update & then redo settings.

---

### Post by SUPERFITTER on 2019-02-19
I think it is the battery that maintains settings in the CMOS memory on the motherboard.  I turn off the power to the computer every night.  The original version of Ubuntu was 14.04 when it was built, that's 5 years old. Time seems to just fly by.  rbmorse may have hit the nail on the head, with his answer.  I will leave the power on over night and see if that works when I boot in 24 hours.  Keeping my fingers crossed and will let you know tomorrow.

---

### Post by SUPERFITTER on 2019-02-20
It was the CMOS battery, the computer booted without a BIOs reset.  Ordered **Sony CR2032 Lithium 3V Batteries (2 x Pack of 5) $5.63 with free shipping,                         **from the Wall.

Thank You for your help.

---

