---
title: "sector read failure after upgrade"
date: 2013-08-29
forum: General Help
---

### Post by a.m.wink on 2013-08-29
Dear all, 

This error on my laptop has left me puzzled: after an upgrade from Quantal to Raring, nothing came up but a blank screen. After ~1 min or so it says: 
error: failure reading sector 0x2900 of `hd0' 
and goes to 'grub rescue' mode.

The only commands I can figure out are 'set' and 'ls'. 
-- 'set' gives:
root=hd0,msdos1
prefix=(hd0,msdos1)/boot/grub
-- 'ls' gives:
(hd0) (hd0,msdos5) (hd0,msdos1) (hd1) (hd1,msdos2) (hd1,msdos1)

In other words, hdo,msdos1 is my root partition. But then when I do 'ls (hd0,msdos1)' it gives me the same error about that sector.

Does anyone know
* if grub is installed correctly in the raring upgrade? is seems very unlikely (but possible) that grub being installed on a bad sector happens during a distibution upgrade (stranger things do still happen during these upgrades)
* if it is possible to repair that sector/move grub to a safe new place without having to reformat/reinstall etc (e.g. boot-repair?)

many thanks

---

### Post by tgalati4 on 2013-08-29
You can boot on another partition if this is a dual-boot system:

```
root=hd1,msdos2
boot
```

It's possible that your drive has a bad sector in the Master Boot Record (MBR), which makes it difficult to use for booting.  Boot a LiveDVD session and use gparted to set the boot partition flag to the second partition and install GRUB to that partition.  Then when you boot, GRUB should come up normally, but it is being read from the second partition.  I normally install GRUB to the first two partitions as a backup for GRUB--just for this situation.  I have a USB Flash keyring that I use for emergency boot to reassign the boot flag from 1 to 2 to get around this issue.

---

### Post by a.m.wink on 2013-10-04
I still have no idea what caused this, but I solved it with booting via the boot-repair disk and manually mounting the root partition.

It turned out that the directories had been moved to a lost&found directory, with new names. 

Luckily on the root directory level there are only a few names to find (/usr, /home, etc) and it was not that hard.
It took a bit longer to finish the upgrade (continuing straight to saucy salamander) with some familiar-looking problems (video driver etc) but none that were disc-related.

This manual fix took a fair bit of work, means that I still don't know what the problem was, and I came this close to going back to good old debian.
In the end though it dit turn out that if the path names are restored, and Linux boots up again as if nothing happened :)

---

