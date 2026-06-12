---
title: "&quot;end kernel panic - not syncing: Fatal exception in interrupt&quot;"
date: 2021-01-14
forum: General Help
---

### Post by littledj on 2021-01-14
After having many issues with Ubuntu 19.10-20.04 (font was scaled really small, computer sometimes froze during power off, had to reinstall grub menu a few times), I decided to completely erase the disk and install Ubuntu 20.10. The first installation failed and brought me to a bug reporting website and stated that currently enabling "install third party software" caused the installer to crash. I was able to have a successful installation the second time. But after running "sudo apt-get update" and "sudo apt-get upgrade," I attempted to reboot my system to apply the updates and I got this. It happens every time I try to reboot/turn off my PC, causing to have to do a hard shut down. I've tried reinstalling Ubuntu 20.10 with no luck. I've also tried troubleshooting it myself and can't seem to find much info on this error. So I'm completely stumped as to what to do now. (I'm on mobile so sorry if the formatting is weird)

[http://imgur.com/a/tkFRpGb](http://imgur.com/a/tkFRpGb)

---

### Post by jadenharrisontaylor on 2021-01-14
You have to complete uninstall and reinstall ubuntu sadly thats the only way you can fix it.

---

### Post by littledj on 2021-01-15
Did you not read my post?

---

### Post by QIII on 2021-01-15
Is our machine set to boot BIOS/Legacy or UEFI?

Did you attempt to install in BIOS/Legacy or UEFI mode -- that is: did you create an EFI boot partition?

---

### Post by deadflowr on 2021-01-15
Could you possibly post some information about the hardware involved?
Anything really, like cpu or gpu or hard drive.
Long shot, but some hardware may require additional settings invoked in order to run smoothly, or at all.

---

