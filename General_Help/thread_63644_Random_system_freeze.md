---
title: "Random system freeze"
date: 2005-09-08
forum: General Help
---

### Post by Hanj on 2005-09-08
The last couple of weeks my system (I'm running Hoary) has completely died under mysteriuos circumstances on several occasions. What happens is basically that I leave the computer, the screensaver goes on, then the screen goes blank (power saving) and when I get back at the computer it won't react. No response at all to mouse and keyboard, and I have to reboot.

This started happening a couple of weeks ago (never had this problem before), and it happens once every couple of days. I haven't noticed any patterns (like, a program that is always running when it freezes or something), except that is only freezes when in power saving mode.

I know this is vague, I'd be more specific if I could. Is there some log file I could check to see which program is causing this? Any help would be appreciated. Not having to reboot all the time is one of the top reasons I chose Linux over Windows.

---

### Post by rafakl on 2005-09-08
Try turning ACPI off.

You need to edit GRUB start parameters and add acpi=off.

---

### Post by Hanj on 2005-09-09
I'm not 100% sure on how to do that. I suppose I edit /boot/config... and change some of those ACPI params? I can't see one named simply "acpi" that I could set to off.

I doubt this will help though. I never had this problem before. I don't see how acpi would suddenly freak out on me like that.

---

