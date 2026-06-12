---
title: "Filesystem permissions"
date: 2007-09-18
forum: General Help
---

### Post by arhimmel on 2007-09-18
For some reason i cannot write to any file on my system or create new ones.  when i try to update my system it gives me an error that it cannot write to a read-only system.  how can i fix this?

---

### Post by dcstar on 2007-09-18
> **arhimmel said:**
> For some reason i cannot write to any file on my system or create new ones.  when i try to update my system it gives me an error that it cannot write to a read-only system.  how can i fix this?

A reboot will fix this if the root filesystem was mounted r/o for some reason.

If this did occur, then a fsck may need to be run on the filesystem.

---

### Post by BLTicklemonster on 2007-09-19
Isn't there a live cd trick to fix this? I did it once, but can't find the way to do it for the life of me.

---

### Post by arhimmel on 2007-09-19
i will try this.  the other problem i have is that sometimes when i am booting up the computer does not find grub and i need to restart a couple of times to get it to actually boot grub and then ubuntu.

---

