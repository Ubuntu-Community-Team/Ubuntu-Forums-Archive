---
title: "Laptop keyboard and touchpad no longer work at GRUB menu or after live disk boot"
date: 2013-04-09
forum: General Help
---

### Post by DJLamar on 2013-04-09
Hi all,

today I started up my laptop as usual and hit enter at GRUB to load Ubuntu (12.04 64 bit). After a minute or two, nothing had happened (and it has SSD drives so usually the login screen appears in a second or less), so I forced the laptop to power down using the power button. When I restarted the laptop, GRUB loaded, but my keyboard had no effect on anything. I believe I checked the BIOS menu as well and the keyboard wouldn't function there either. However, even a USB keyboard will not have any effect at the GRUB screen, and either I've had the auto-boot timer off in GRUB and haven't noticed it, or something else is disabling it.

I can boot into a live disk, which is what I'm using to type this currently, and then an external keyboard and mouse work fine, but the laptop's keyboard and mouse still don't work. Note that this computer has a RAID 0 setup, so I can't use the standard installer to reinstall Ubuntu. I used the alternate installer before, but I tried loading that now and in there as well not even an external keyboard and mouse will work, so as far as I can tell, reinstalling is not an option. As an FYI, my laptop runs UEFI, and I was only able to get Ubuntu running by setting it to legacy BIOS mode and installing Ubuntu in legacy mode.

Could this be anything other than a hardware problem? I just bought this computer less than a month ago, so a hardware failure this early in its life would be pretty bizarre.

---

### Post by franzvomsee on 2013-04-29
I had a similar problem with a new Sony Vaio. Keyboard and touchbad was dead, external KB and mouse worked fine. I found the following remedy and it worked:
remove battery
hold down power button for 60 seconds
boot without battery

After another reboot with battery, everything worked fine.

---

