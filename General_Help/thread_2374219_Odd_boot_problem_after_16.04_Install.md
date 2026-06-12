---
title: "Odd boot problem after 16.04 Install"
date: 2017-10-13
forum: General Help
---

### Post by matthew54 on 2017-10-13
After running updates on a 16.04 machine that my university uses for digital signage, I have been having trouble getting it to boot correctly. I did a full reintstall of 16.04 to try to fix the issue but it is still happening.

Here are my steps: 
1. Install OS
2. Do a reboot
3. Hangs at purple blank screen forever
4. Hard reset
5. Tap shift to get to grub
6. Press down arrow to move cursor and move it back up to choose the default option
7. Boots fine - Confusion!

So on its own it gets to the blank purple screen and won't boot, but if I go to grub and even just move the arrow keys, it will boot fine. Is something not loading in time and then doesn't get loaded at all? This is one of the stranger issues we've had.

This machine is is an MSI Cubi2 007BUS

---

### Post by oldfred on 2017-10-13
Other MSI systems need boot parameters.
And often UEFI is similar by brand so many models need similar settings.
But yours is a lot different, not sure if any of this applies or not?

 MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)
Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)

---

