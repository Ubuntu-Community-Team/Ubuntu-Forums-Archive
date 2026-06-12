---
title: "Ubuntu 14.04 on USB External Drive Win 8.1"
date: 2014-07-08
forum: General Help
---

### Post by rickm1945 on 2014-07-08
I have Ubuntu on a USB External HD which was running fine on a Dell win7 desktop computer. I how have a Asus which has a UEFI Secure Boot instead of BIOS. Anyone got an idea as to how I can get the usb to boot? In the UEFI I don't see anyway to chance boot options. It only shows Windows boot which s drive C. CAn I disable UEFI and choose Other OS and be able to see the other options?

---

### Post by Vladlenin5000 on 2014-07-08
If you disable UEFI and the installed OS has been installed in that mode, it won't boot. And I'm almost sure you can't boot the external HD originally made for a classic BIOS in a new system with UEFI.
Bottom line: If your intention is to use it on both I think you're out of luck.

---

### Post by rickm1945 on 2014-07-09
When in the UEFI make sure Legacy is enabled. 
I figured it out. In UEFI get in advanced mode. Disable fast boot, Down towards the bottom of screen under setup mode you will see CSM (Compatibility Support Mode) click on that and enable it. Press  F10 and exit. Reboot with the USB HDD plugged in, and go into UEFI once more ( On my computer I press and hold the Delete Key or F2) this may vary)  it should show the device in the first screen, near the bottom,  you can then  move the USB HDD to the first position by just clicking and dragging it Press F10 to Save and Exit. hope this helps someone else with the same problem. My Ubuntu 14.04 is up and running Hurrah, Hurrah!!!!!!

---

### Post by sudodus on 2014-07-09
Thanks for sharing your method :-)

It is also possible to make a USB drive that can boot in both UEFI and BIOS mode. See this link

[Portable installed system that boots in UEFI as well as in BIOS mode]("http://ubuntuforums.org/showthread.php?t=2213631")

---

### Post by rickm1945 on 2014-07-09
Sudodus, thanks for the information I have bookmarked the pages. An interesting and workable USB solution .

---

