---
title: "GB P35C-DS3R 64 bit gutsy 7.10 boot crash and solution"
date: 2008-02-16
forum: General Help
---

### Post by elokide on 2008-02-16
Just want to make this info easily available since it took me a while to pinpoint it. Apparently this board doesn't work only because i've upgraded the bios as others have had success "out of the box". Didn't post a bug report cause it's most likely the BIOS that's doing something wrong not the OS.  First the problem, last paragraph for the solution.

I'm running BIOS F10 on a rev 2.0 board and it crashes almost always upon booting 64-bit 7.10 (i was lucky enough to have it work once and it get installed off the live CD). The 32 bit version seems to install fine although i only booted into the livecd environment. The only thing close to an error i saw was that DSDT was not found during boot. I tried running acpi=off noacpi (since DSDT shows up under ACPI during boot) but with no solution. Regardless of the missing DSDT it would only crash amd immediately restart directly after "checking if image is initramfs ... it is". 


THE SOLUTION to the entire problem was to disable legacy USB devices in BIOS. Disable both keyboard and mouse. Boots every time now after much testing. it has nothing to do with my drivers etc. in fact my sound, video, everything works just great as i expected from this amazing OS.
hope this helps. enjoy guys :popcorn:

E6550 stock
P35C-DS3R rev 2.0 stock audio, ethernet, everything.
2GB
ATI 1650XT


**sorry guys i could have swore i put this under hardware and not general help>.< should i repost it there?**

---

