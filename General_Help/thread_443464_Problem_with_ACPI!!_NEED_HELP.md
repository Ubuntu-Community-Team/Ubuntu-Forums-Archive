---
title: "Problem with ACPI!! NEED HELP"
date: 2007-05-14
forum: General Help
---

### Post by gashcr on 2007-05-14
My neighbor box got infected with a virus, and now he has a problem with, apparently his BIOS. The virus ruined his PC, so he tried to reinstall XP, but the system denied to install due some hardware problems. Then, I tried to install Edgy, but I got a Kernel panic...
I tried feisty, and something happened... It told me the BIOS age was 1906, and had no cutoff for 2000. So, it would force ACPI. Then, everything went the normal way. 

Now, everytime the system starts, it shows the same message, and it won't shutdown properly... after umounting the system file, it halt, and it requires a hard power down...

Any way you know we can solve this?? Is it too serious??

---

### Post by yopnono on 2007-05-14
> **gashcr said:**
> My neighbor box got infected with a virus, and now he has a problem with, apparently his BIOS. The virus ruined his PC, so he tried to reinstall XP, but the system denied to install due some hardware problems. Then, I tried to install Edgy, but I got a Kernel panic...
I tried feisty, and something happened... It told me the BIOS age was 1906, and had no cutoff for 2000. So, it would force ACPI. Then, everything went the normal way. 

Now, everytime the system starts, it shows the same message, and it won't shutdown properly... after umounting the system file, it halt, and it requires a hard power down...

Any way you know we can solve this?? Is it too serious??

What is the BIOS date/time set to? also does it loose the time every time you shutdown, them it might be the (BIOS) battery.

---

### Post by gashcr on 2007-05-14
It is set up to date, and the PC was bought fairly a pair of months ago, so I don't think the problem to be that

---

### Post by jerrylamos on 2007-05-14
May not be of any use, but boot options "noapic acpi=off" might help.  Go into /boot/grub/menu.lst (where l is lower case L) and on the first kernel line look for it to end:
kernel .....blah blah .......quiet splash

Change it to:

kernel .....blah blah .......quiet splash noapic acpi=off

May or may not have an effect.  You could test it by booting CD Live, on boot menu choices push F6 then make the additions after quiet splash.

Now there is an outstanding bug on Feisty where it doesn't shut down on some computers like this one.  In my post "Workarounds" on "Installation & Upgrades" there is a workaround for that, open the post and look for "Shutdown doesn't".

Cheers, Jerry

---

### Post by gashcr on 2007-05-14
Thanks a lot, I will try that to see if it works

---

