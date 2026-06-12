---
title: "Acer Aspire ES 15 - no bootable device, help"
date: 2020-11-18
forum: General Help
---

### Post by tackskull on 2020-11-18
Today I was trying to install Ubuntu on this laptop erasing the  entire hard disk drive. When the installation was complete, I rebooted  the laptop e suddenly the message "no bootable device" appear, and now I  am stuck. 

I tried everything:
- I went to the BIOS and changing the boot from UEFI to Legacy, nothing change
- I ttied to go in the BIOS and reset the default setup of the BIOS, nothing change

- I tried to adjust the clock in the BIOS to the current time, nothing change
- I tried to format the hard disk, nothing change
- I tried to use another internal hard disk drive, nothing change
-  I tried to install other linux distro, and when the installation is complete, I  reboot the laptop and I am always stuck on the "no bootable device"  message



Everything I do I am always stuck.


Can somebody help me?

---

### Post by oldfred on 2020-11-18
Many have had to upgrade UEFI and if SSD update SSD firmware.
But you need to set "trust" on Ubuntu entry which now is shown as unknown.

These are all essentially the same, one or other may explain it to you a bit better.
Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)

---

### Post by tackskull on 2020-11-19
Wow thanks a lot :D I followed the solution of the 4th link and everything works well now :D

Thanks :D

---

