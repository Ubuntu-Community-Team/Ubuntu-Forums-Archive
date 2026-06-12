---
title: "boot problemas after backup restore"
date: 2007-07-26
forum: General Help
---

### Post by nomad5000 on 2007-07-26
I made a backup of my linux partition with the tar command. I repartitioned my hard drive and reinstalled grub.
now when I boot I get everything working corectly untill the following error message comes up. 

Check root= bootarg cat /proc/cmdline
or missing modules, device: cat /proc/modules ls /dev
ALERT! does not exist. Dropping to a shell

what does this mean?? and how can I fix it?

Thanks for any help!!!

Michael

---

### Post by dcstar on 2007-07-27
> **nomad5000 said:**
> I made a backup of my linux partition with the tar command. I repartitioned my hard drive and reinstalled grub.
now when I boot I get everything working corectly untill the following error message comes up. 
.......l

I'm not sure **tar** will back up various symbolic links and/or critical system files, so using this in the way you have may not result in a working system.

You may have to do a fresh install, and then use your tar file to replace the default files with your saved ones (and hope that you don't break the install).

---

