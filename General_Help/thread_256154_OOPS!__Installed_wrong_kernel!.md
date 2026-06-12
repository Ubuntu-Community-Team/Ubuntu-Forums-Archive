---
title: "OOPS!  Installed wrong kernel!"
date: 2006-09-12
forum: General Help
---

### Post by Orbit45244 on 2006-09-12
I was following the guide [here]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper") to install the Nvidia drivers for my card.  The only problem was that I was using the 386 kernel, but I accidentally installed the k7 kernel, and now it's on my system, and it's in my list of OS's in GRUB.  I was wondering if I should be concerned about this, and how I can uninstall the k7 kernel, but leave the 386 one intact, and how I can get the k7 one off of my OS list.  I tried uninstalling the package, but the k7 kernel is still on my system.

---

### Post by moore.bryan on 2006-09-12
*if you already removed it, ```
sudo update-grub
``` if it's still there, edit menu.lst in /boot/grub/ and remove it.*

---

### Post by Orbit45244 on 2006-09-12
> **moore.bryan said:**
> *if you already removed it, ```
sudo update-grub
``` if it's still there, edit menu.lst in /boot/grub/ and remove it.*
I just uninstalled the package for the k7 kernel, and "sudo update-grub" says that it found the k7 kernel, in the output.  And the entry for the k7 kernel is still there, so I'll just delete the entry.

---

