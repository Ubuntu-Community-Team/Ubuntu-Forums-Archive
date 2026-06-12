---
title: "Upgrading to Nvidia GT610 Video Card"
date: 2014-05-05
forum: General Help
---

### Post by Gilad_Pellaeon on 2014-05-05
Here's something I want to ask for those of you more familiar with video card upgrades with Linux. I've ran windows for a lot of years and i'm curious is there anything I need to know to install and start using the Nvidia propriearity video driver in Xubuntu 14.04? I'm hoping to upgrade my Dell desktop from Intel i945 graphics to an Nvidia GT610 video card in the near future, and I know with windows it's usually a case of switching off the integrated graphics in the bios, turn off machine, install the video card, and then reboot into windows and install the video driver.

Now my question is, will Xubuntu 14.04 (32 bit version) act the same way and allow me to install the nvidia driver or is there any commands i'll have to do in the terminal with sudo to download and install nvidia's official driver? I've never done this before with Linux so this is why i'm asking so I won't have any suprises come upgrade time where I can't get into my Xubuntu install and have a working display to install nvidia drivers.

---

### Post by Elfy on 2014-05-05
Turn it off, fit the card, turn it on - Settings Manager - Additional Drivers - let it find nvidia drivers - install that - it will ask for password - reboot.

---

### Post by oldfred on 2014-05-05
You will need nomodeset to be able to boot into system, then follow Elfy's suggestions.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Gilad_Pellaeon on 2014-05-05
> **oldfred said:**
> You will need nomodeset to be able to boot into system, then follow Elfy's suggestions.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Ahh ok that seem's easy enough to do then by changing quiet splash to nomodeset and then just following Elfy's suggestion. With nvidia's own driver's it sounds like I may not to need make nomodeset a permanent option so i'm hoping that's the case at least after reading the link you provided. :)

---

