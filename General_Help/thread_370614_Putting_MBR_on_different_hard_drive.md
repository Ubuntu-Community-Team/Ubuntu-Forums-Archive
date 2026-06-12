---
title: "Putting MBR on different hard drive"
date: 2007-02-25
forum: General Help
---

### Post by MikeBrandman on 2007-02-25
I just installed ubuntu on my laptops external drive, but now if I unplug my external and boot up, I get GRUB Error 21.  Is there anyway I can put MBR on my laptops internal drive or make it somehow automatically boot into XP when the external is disconnected?

---

### Post by rsambuca on 2007-02-25
You have a couple of options that I can think of off-hand.  You can remove grub from the laptop's harddrive and use the bios to pick the boot drive every time, or you can add a small /boot partition to your harddrive and install grub there.

---

### Post by dcstar on 2007-02-25
> **MikeBrandman said:**
> I just installed ubuntu on my laptops external drive, but now if I unplug my external and boot up, I get GRUB Error 21.  Is there anyway I can put MBR on my laptops internal drive or make it somehow automatically boot into XP when the external is disconnected?

There are HOWTOs in the forum on re-installing Grub, it should be possible to follow those detailed instructions and do what you want.

You could also just restore the internal drives MBR with the Windows "fixmbr" utility, and actually have Grub on the external drive just for Linux use.

---

### Post by Azakus on 2007-02-26
Try this: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by orb9220 on 2007-02-26
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

