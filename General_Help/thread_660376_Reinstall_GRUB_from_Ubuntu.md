---
title: "Reinstall GRUB from Ubuntu"
date: 2008-01-06
forum: General Help
---

### Post by YodaMstr on 2008-01-06
Ok, so, I reinstalled Vista, and now my GRUB isn't working.  So I installed a second instance of Ubuntu on a separate partition, and then I scroll to my original Ubuntu.  Is there any way I can get rid of this second install of Ubuntu and make my original install be the primary OS when GRUB starts?

---

### Post by dcstar on 2008-01-07
> **YodaMstr said:**
> Ok, so, I reinstalled Vista, and now my GRUB isn't working.  So I installed a second instance of Ubuntu on a separate partition, and then I scroll to my original Ubuntu.  Is there any way I can get rid of this second install of Ubuntu and make my original install be the primary OS when GRUB starts?

You can change Grub to do many things, in a terminal:
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by danwood76 on 2008-01-07
You can reinstall grub from the live CD, no need to do a full installation.

What I would do is boot the live CD and delete the second install of ubuntus partition (make sure 100% that you delete the correct one)

Then reboot and reload the live cd and reinstall grub using this guide:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

regards,
Danny

---

