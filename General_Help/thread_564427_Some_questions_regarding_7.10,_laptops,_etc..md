---
title: "Some questions regarding 7.10, laptops, etc."
date: 2007-10-01
forum: General Help
---

### Post by foundation on 2007-10-01
Ok, I'm going away for a few weeks and will be taking my dad's laptop and I'm going to install Ubuntu on it (It already has XP but I want both available to use) so I have some questions:

- If I install Ubuntu it will simply install GRUB too and Win XP will be automatically added? Also, if I get rid of the partition which has Ubuntu will XP boot fine?
- I want the improvements in 7.10 but it's in beta, do you think I'd be fine using it for ~2 weeks (Not heavy use and will just be basic email, browsing, etc) and would an upgrade to the final version go cleanly?
- How well will suspend/hibernate (Like, when I close the laptop lid) work or is this dependent mostly upon the laptop?
- Any suggestions for Linux use on a laptop as this will be the first extended use of Linux on a laptop by myself.

Thanks guys. :)

---

### Post by ramjet_1953 on 2007-10-01
Yes, you can install Ubuntu as a dual-boot system and Windows will be an option to boot into from the GRUB menu.

Remember, however, if you decide to remove Linux and GRUB at a later date, you will need your Windows disk and boot in recovery mode, to fix the Windows MBR.

Don't forget to defragment the Windows HDD 2 or 3 times, before installing Ubuntu.

Providing you don't install anything outside of the standard Ubuntu repositories all should go well with a system upgrade. Do not use Automatix.

Suspend / Hibernate functionality will depend upon which lappy you have.

I suggest that you have a good play with what comes as standard, at first and then branch out, after you are feeling more comfortable.

Issues that may arise are the need to install a graphics driver to enable widescreen and optimum resolution and colour depth and enabling wireless networking.

Here is a link that covers most things that you will need:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Regards,
Roger :cool:

---

### Post by mikewhatever on 2007-10-01
I'd say, don't go installing operating systems on your dad's laptop for two weeks. Use what it already has and return it safely.

---

### Post by anaconda on 2007-10-01
When you install ubuntu windows should be automatically added to the linux bootloder (GRUB)

And yep. when you remove linux the Grub bootloader wont work any longer, because part of is in linux partition. 

That is unless you make a separate /boot partition (~50-100MB) The bootloader will be installed to the /boot partition, which you wont destroy when destroying ubuntu..

---

