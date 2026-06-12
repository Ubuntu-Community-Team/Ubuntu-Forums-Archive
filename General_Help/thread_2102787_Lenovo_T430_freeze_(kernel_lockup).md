---
title: "Lenovo T430 freeze (kernel lockup)"
date: 2013-01-08
forum: General Help
---

### Post by instantmove on 2013-01-08
Before writing a solution I'll describe the problem a bit and solutions I've tried.

Couple month ago I've decided to change my laptop from Dell Latitude E6420 to Lenovo T430s as during the last half of the year Dell was always freezing and it was very difficult to work with it. Freezes started after system update, and my mistake was to make fresh install instead of trying to revert or investigate something... So I've bought Lenovo T430s (without nvidia), SSD drive, 16GB memory and installed Ubuntu 12.04. 

It was a big surprise when after using it for a while it freezed on T430s. But as I liked it more, I decided to find solution of freezes anyway. I've read tons of articles and installed every possible new kernel for ubuntu, have made about 20 fresh installs, updated bios, firmware, installed microcode, compiled intel drivers myself, but it was freezing and sometimes it seemed that several reasons lead to such result...

By freeze I mean complete lockup, so no mouse moving, can't ssh from another machine, even REISUB, don't work, only pressing power button for several seconds helps. Freeze appeared after random time, it could be 5 minutes, it could be 2 hours, and mostly on low load.

After reading thread similar to [**this one**]("http://ubuntuforums.org/showthread.php?t=2076245") I've started to think about changing motherboard, but Lenovo support forums claimed that problem had been fixed for all machines produced after September 7th, mine was produced September 9th =) Plus Windows 7 was working fine, even for couple days, so I had no evidence of hardware fault. But support changed me wi-fi card to more advanced as when using lan system was rynning without freezes for much longer.

Ok, so after nearly a month of experiments I've got configuration which was not freezing for a couple weeks, but there was a problem with power consumption using a battery... no ideal thought.
I've installed TLP to fix this and made some changes to BIOS configuration, after some time it started to freeze again.. but as I've changed a lot (including new kernel install) it was difficult to understand why.

Yesterday, I've made final conclusion about the culprit, but it looks weird for me. All I've done was disabling "CPU Power Management" from BIOS. I have fresh install of Ubuntu 12.10, kernel 3.7.1 (also tried legacy, 3.6.8, 3.6.11, 3.8-rc2), no TLP, no special modules, and system doesn't freezes only if I go to BIOS and disable setting..

Unfortunately I don't have Dell anymore, so I can check it on another machine, but on Dell there is older hd3000 video and older CPU, so solution could be just updating a kernel.

Even if this is solved for me, I'd like to report about it to kernel team, but can anybody help me to understand is it possible that BIOS and kernel tries to manage CPU frequency simultaneously? Or at least any ideas why freezes disappears after disabling "CPU Power Management" setting in BIOS would help a lot. 

Thanks!

---

### Post by Chris_82 on 2013-03-06
Congratulations to finding the workaround!

I have also bee struggling for some time with a hard freeze on a Lenovo Thinkserver E30 with no luck so far.
Fresh install of 13.04.
What I tried:
- BIOS update
- SSD firmware update
- changed PCI wifi card to USB stick

When frozen the machine does not react to Ctrl-Alt-F1 or REISUB magic keys.
I will try to dig up the BIOS CPU Power Management.

---

