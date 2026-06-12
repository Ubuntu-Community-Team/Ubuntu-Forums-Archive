---
title: "plymouth during boot problem"
date: 2012-11-30
forum: General Help
---

### Post by elguavas on 2012-11-30
during bootup, on my system with the radeon kms driver, my displays turn off (both showing 'no signal' messages) between grub and lightdm.

grub displays normally, lightdm graphical login displays normally and x displays and works normally. the plymouth progress screen displays normally during shutdown.

can anyone give me some advice on how to troubleshoot why plymouth won't display a progress screen during bootup?

i'd at least like to be able to force a text mode plymouth to display during boot, if the graphical one can't be gotten working, so that i will actually _see_ something if/when the system runs fsck during boot or whatever.

tia for any replies.

---

### Post by Rebelli0us on 2012-11-30
I don't have the foggiest what plymouth is, but I have the same, [no disk check progress]("http://ubuntuforums.org/showthread.php?t=2088105") just a blank screen, and if a disk will not mount the "press S to skip" is not seen so the system appears hung with just black screen.

That was with AMD gpu, then I installed a NVIDIA card and now I get basic status in text mode but no graphic progress. StartUp-Manager would fix it but it's no longer available.

---

### Post by elguavas on 2012-11-30
> **Rebelli0us said:**
> I don't have the foggiest what plymouth is

plymouth is the software that ubuntu uses to display the progress screens during boot and shutdown.

as i said it displays normally during shutdown, but just as you described nothing whatsoever displays during boot (between the grub and login screens).

this is also with an AMD gpu, which, as i also mentioned, uses the kms (kernel mode setting) 'radeon' driver.

anyone got any hints on how i can diagnose the problem?

---

### Post by Rebelli0us on 2012-11-30
You can install Grub customizer and remove kernel parameters "quiet splash", that will give you all progress in text mode  (including all the linux techno-garbage spilling on your screen). But I too would like to know how to get nice graphic output without the garbage.

---

