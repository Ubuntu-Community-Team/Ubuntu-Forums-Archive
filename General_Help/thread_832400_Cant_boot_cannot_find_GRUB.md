---
title: "Cant boot cannot find GRUB"
date: 2008-06-17
forum: General Help
---

### Post by amyers22 on 2008-06-17
Hello, I am pretty new to Ubuntu and had installed Ubuntu on a separate HDD. Now the HDD with ubuntu is dead and I cannot load my Windows HDD because it cannot find GRUB. Is there anyone who can provide help with this?

---

### Post by conehead77 on 2008-06-17
> **amyers22 said:**
> Hello, I am pretty new to Ubuntu and had installed Ubuntu on a separate HDD. Now the HDD with ubuntu is dead and I cannot load my Windows HDD because it cannot find GRUB. Is there anyone who can provide help with this?

You might want to reinstall the Windows bootloader which is ms-sys. If you have a Ubuntu live-CD try this post:
[http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)
(You need to know the partition where windows is installed, you can get the information with a partition program, for example gParted (dont know if its on the live-CH)).
Also this doesnt seem to work with Windows Vista.

Another possibility: Boot into the Windows recovery-CD, there should be a option "startup-recovery" somewhere. Good luck!

---

