---
title: "Dual Boot error with Ubuntu 20.04.1 LTS"
date: 2020-08-18
forum: General Help
---

### Post by ornelas1998 on 2020-08-18
[FONT=Ubuntu]Hello fellow Ubuntu users and enthusiasts!

I've had an issue that I could not solve in my computer running a dual boot consisting of my mainly used OS being [/FONT][FONT=Ubuntu]Ubuntu [/FONT][FONT=Ubuntu]20.04.1 LTS[/FONT][FONT=Ubuntu] and[/FONT][FONT=Ubuntu] the other one Windows 10 [/FONT][FONT=Ubuntu]which I use for gaming purposes.[/FONT][FONT=Ubuntu]
When I restart my computer on the Windows side, and then trying to switch to Ubuntu, at some point in the boot, the system will freeze, forcing me to shutdown using the power button.

Has anyone had the same issue? I'm seeking help to solve it or at least bring the issue to try to help my favourite Operating System with my feedback.

Thank you all very much and king regards,
Luís Ornelas[/FONT]

---

### Post by von Stalhein on 2020-08-21
What boot manager are you using?
Are the OS's on separate drives or in partitions on one drive?
Is it a UEFI system?

---

### Post by CelticWarrior on 2020-08-21
And have you disabled Fast Startup in Windows? Recommended even if Windows standalone and a must if dual-booting.

PS - I think I know who you are, Mr. Ornelas ;) Does the name Vanessa Hallberg means something to you?

---

### Post by ornelas1998 on 2020-08-25
Hello! I haven't tried to disable, I transitioned to dual boot fairly recently, so I am on the process of learning my best settings, but I'll make sure I do!
I'm not remebering, sir CelticWarrior :-s Can you PM me more information?
Thank you for your reply!

---

### Post by ornelas1998 on 2020-08-25
Hello Mr. Stalhein! I have partitioned my HDD to allocate Ubuntu and I am using GNU GRUB 2.04 as boot manager.
It is EFI from what I can tell with my verifications.
Thank you for your reply!

---

### Post by von Stalhein on 2020-08-26
Hi!

If you are unable to boot in to Ubuntu at all, try booting using a USB stick made in Win10 using [these instructions ]("https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview")

Then attempt to repair the GRUB menu with [URL="https://www.fosslinux.com/4477/how-to-repair-the-grub-bootloader-using-a-ubuntu-live-usb-drive.htm"]this method
[/URL]
**If** you can log in, run```
sudo apt update
``` then ```
sudo apt dist-upgrade
```

then ```
sudo update-grub
``` Hopefully that will sort it.

Please let us know if that makes any difference & if not we'll try some other things.

Good luck!

---

