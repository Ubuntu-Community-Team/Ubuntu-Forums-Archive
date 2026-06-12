---
title: "Grub error 16 = brick"
date: 2006-11-15
forum: General Help
---

### Post by djsamsel on 2006-11-15
i had a system crash that required a hard reboot of the system. i know get grub error 16 when i try to boot into any os (U or XP). i found this out, 

"Inconsistent filesystem structure - This error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB."

and have tried to reinstall grub using this page [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

but still get the same error. any help will be greatly appreciated. doug

i found super grub at  [http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)  
i removed grub, then reinstalled it, then booted directly from super grub into linux. there were a bunch of filesystem errors that were repaired. i then rebooted without super grub installed in the cd-rom and from grub was able to boot normally

---

### Post by djsamsel on 2006-11-16
bump

---

