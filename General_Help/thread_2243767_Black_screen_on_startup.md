---
title: "Black screen on startup"
date: 2014-09-11
forum: General Help
---

### Post by allosaurus029 on 2014-09-11
I set up new laptop (Thinkpad T440) to dual-boot Xubuntu 14.04.1 and Windows 8. I've been using the laptop for a week without any problems until now. I cannot use the computer at all, I just get a black screen on startup (no GRUB, no login, nothing).

This started after I locked the screen, walked off for a while, and tried to wake it up. It showed the login screen momentarily, then went black. Nothing would wake it up, so I tried to reboot it, but I keep getting a black screen. I have no idea what to do.

If it matters, IIRC there were updates that required a restart to take effect, and I suppose they would have taken effect since I tried to restart.

---

### Post by kansasnoob on 2014-09-11
Do you have the live USB you used to install Ubuntu? If so see if it'll boot, then we'll have to put our thinking caps on ............ may be tough since you can't get to the grub boot screen :(

If you should have to reinstall Ubuntu beware of this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Not sure how helpful it would be but maybe Boot Repair's boot info link would provide some clues:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I would not run the recommended repair though until we've had time to look over the boot info.

---

### Post by allosaurus029 on 2014-09-11
I have the live USB, but I can't even see BIOS or anything. So I don't know how I could boot from USB.
As for the UEFI issues: yeah, I spent quite some time wrestling with that when I set it up :)

---

### Post by kansasnoob on 2014-09-11
My sons newish Dell occasionally does that - displays no BIOS - and he has to remove the battery and walk away for a few minutes. Then when he puts the battery back in it starts working again. Doesn't happen often - three times in nearly a year.

---

### Post by Bucky Ball on 2014-09-11
When you are looking at that black screen, can you hit control+alt+F1. What happens?

And, yes, as kansasnoob suggests, switch off, take the battery out and hold down the power button (with the machine completely unplugged and the battery out) for about 30 seconds/a minute. Resume fixage ...

---

### Post by allosaurus029 on 2014-09-11
I finally figured out that my backlight is broken -- if I shine a flashlight at my screen, I can see it. Which I guess is a lot better than some things that could have happened, but I'm still pretty lost. This page:
[https://wiki.ubuntu.com/Kernel/Debugging/Backlight](https://wiki.ubuntu.com/Kernel/Debugging/Backlight)
says "If you have an issue where backlight stops working after suspend or hibernation, please see their respective debugging article.", but I don't know exactly which debugging article it's talking about and it doesn't seem to have any links. Has anyone else had this problem? Is it possible there was something wrong with the update I installed prior to restarting that caused this?

---

### Post by kansasnoob on 2014-09-13
I'm clueless but I'll give you a free bump.

---

