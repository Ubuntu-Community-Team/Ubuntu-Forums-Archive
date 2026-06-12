---
title: "grub, GRUB_CMDLINE_xxx, ipv6, and multiple OS's"
date: 2019-08-22
forum: General Help
---

### Post by aeronutt on 2019-08-22
Summary:
I'm trying to disable ipv6 via grub. I have multiple OS's.  My changes to grub to disable ipv6 take effect in the OS where I run grub, but not in other OS's.  

Details:
OS #1 (Ubuntu 18.04) is where I edit grub, update-grub, etc. In this OS, I tried 2 things in /etc/default/grub
GRUB_CMDLINE_LINUX="ipv6.disable=1"
and
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ipv6.disable=1"

Both attempts disabled ipv6 in OS #1, but do NOT disable ipv6 when I boot into OS #2 (KDE).
(I check ipv6 with ifconfig.)

I thought those kernel parameters got passed to which ever kernel was booting??

---

### Post by DuckHook on 2019-08-22
I take it that you are dual booting? If so, then OS#2 is likely using a different bootloader and initram image than OS#1. To synchronize the two, you will need to boot into OS#2, change *its* grub to have the proper kernel parameter, then run:```
sudo update-grub
```
Then, reboot into OS#1 and:```
sudo update-grub
``````
sudo grub-install
```
I *think* that will do it, but it's been a long time since I've had to do something like this and the ole' noggin is gettin' forgetful.

---

### Post by aeronutt on 2019-08-22
Ok, that worked! Thanks.
Yes, dual boot system.

I didn't know one could 'sync' grub across OS's.  So, what's really happening when I run these commands (relative to getting the 2 OS's grub's in sync)?

---

### Post by DuckHook on 2019-08-22
I indulged in a little descriptive liberty. You weren't actually "syncing" GRUB so much as forcing the creation of a new boot/initram image in OS#2. When you run update-grub, what you are actually doing is forcing the system to build a new initram image using the parameters in GRUB. Because your OS#1 initram is different than your OS#2 initram, if you introduce new kernel parameters into OS#1 GRUB, you will just get them in OS#1 initram. In order to get these kernel parameters into OS#2 initram, you must also reconfigure, then update OS#2 GRUB. Updating just OS#1 GRUB won't do it. 

So, there is no real "syncing" involved.

I believe that fellow Forums member *oldfred* has a method whereby one GRUB can be used for both (or more) OSes, but I can't find the link. I've never really needed it because I'm now in the habit of duplicating all of my kernel parameters in each individual partition that has a Linux OS. Since I have no more than three at a time, I would rather put up with infrequently having to duplicate work over than the complexity of truly "syncing" my GRUB.

---

### Post by aeronutt on 2019-08-22
Thank you very much for the help and description.
oldfred has helped me several times with issues similar to this!
I keep learning. :)

---

### Post by DuckHook on 2019-08-22
For the benefit of posterity and those who follow, I've taken the liberty of marking this thread "solved".

Good luck and happy Ubuntu-ing!

---

