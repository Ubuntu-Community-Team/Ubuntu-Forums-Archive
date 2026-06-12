---
title: "Ubuntu 15.04 Booting Problem"
date: 2015-10-21
forum: General Help
---

### Post by Ben_Rounds on 2015-10-21
After upgrading to 15.04 I tried installing some updates. Upon the restart to finish updating, my laptop no longer boots properly, it stops at a black screen with a terminal like text. I have tried rebooting while holding shift to access the boot options but they never pop up. If you can help me with this issue it would be much appreciated.

---

### Post by oldfred on 2015-10-22
Did you have a proprietary driver installed. And update does not reinstall that. You in effect have to start over on video driver install.

What video card/chip?

Can you boot with nomodeset or recovery mode, second line in grub menu?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

