---
title: "Install Ubuntu on second HD."
date: 2007-08-07
forum: General Help
---

### Post by mastersync on 2007-08-07
Hello!

I really like Wubi and experimented with it a while just now. Ubuntu setup went real smooth and fine, played around with it. I have two HD and my master HD is running windows and second HD is running Wubi/Ubuntu. Dual boot went just fine.

Now I would like to have a dedicated installation of Ubuntu on my second HD, leaving the XP on so I can dual-boot.

Is there anyway I can do this with Wubi ?

Thanks !

---

### Post by logos34 on 2007-08-07
If you now want a dedicated installation of Ubuntu, then burn the ubuntu iso to a cd and install to the second drive--it'll run faster than from within Wubi.  Back up any files on the second disk beforehand.  Go into the Bios and set the second disk as first in the Bios hard disk boot order.  Then run through the guided ubuntu install.  It should put grub boot loader on the ubuntu disk and add a correct entry to your grub config files to allow you to boot windows.  (If all goes right, windows boot loader will remain untouched on the master HD/windows drive).

---

### Post by tuxcantfly on 2007-08-07
If you want to transfer your Wubi install to a dedicated partition without needing a CD or reinstalling, use LVPM here: [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

---

