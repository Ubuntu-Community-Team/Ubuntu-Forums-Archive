---
title: "Wubi broke Windows"
date: 2008-04-12
forum: General Help
---

### Post by Weirdbro on 2008-04-12
Ok, so I downloaded the 8.04 beta .iso, burned it. I had it bootstrap a bootloader so I could use the livecd, because my BIOS was being a pain. I go into the LiveCD, reboot back into windows, and uninstall the bootloader used to help with the LiveCD. Then, I install into Wubi. I reboot, finish the installation, and work in Ubuntu for the day. Then, when I try to reboot into windows, I can't. I try Windows Safe Mode. It shows a list of files being loaded, but it crashes after Mup.exe or something like that. The partition isn't corrupted, and Wubi still works. What could have been broken?

---

### Post by vexorian on 2008-04-12
Try using the XP CD to restore windows' MBR,

fixboot

command.

If it doesn't work, use

fixmbr

Regarding what failed, I have no idea.

You should go to launchpad so to get the devs' attention.

---

### Post by ago on 2008-04-13
Try running chkdsk /r from the windows CD

It could of course be something completely unrelated, you can use wubi also to do a virusscan/access the windows drive in order to check that.

---

