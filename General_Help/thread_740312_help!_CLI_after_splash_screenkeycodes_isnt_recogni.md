---
title: "help! CLI after splash screen/keycodes isnt recognized/8.04 Beta"
date: 2008-03-30
forum: General Help
---

### Post by Thristle on 2008-03-30
well i tried installing with wubi and everything worked fine until i tried to boot up ubuntu.
i can see the splash screen and it looks like its fully loading but then i can only see a command prompt somtimes the last line says "starting ACPI services" and sometimes it writes somthing about a read-only file system
i tried following one of the solutions offered in a similar thread but whenever i press one of the F keys it says "keycodes not recognized "
and it asks me to assign new keycodes...

i tried this a couple of times with a daily build and the beta but i always get the same error

---

### Post by ago on 2008-03-30
Is this after the first reboot?
If so press esc after selecting Ubuntu and try safe-graphic-mode and acpi-workarounds

If it is after the second reboot, press esc and select single user mode.

---

### Post by Thristle on 2008-03-30
if u mean "first reboot" as the one with the installation then its in only in the 2nd boot and up

ok i tried to get into that single user mode but i couldn't find any option even remotely similar...
i should mention that i can only go as far a the grub loader and that the recovery mode is not working either

---

### Post by ago on 2008-03-30
Try the second entry in the menu "recovery mode". That will lend you in a shell. Check that you can r/w files.

---

### Post by Thristle on 2008-03-31
ok tried the recovery mode
it showed some junk but i found out that if i try to press one of the arrow keys i can see a menu
tried all the options
"try to fix the X..."-does nothing
and using the command line only shows input/output error

---

### Post by ago on 2008-03-31
Can you take a screenshot of what you see?

---

