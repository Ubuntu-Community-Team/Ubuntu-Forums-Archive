---
title: "external drive mounted twice"
date: 2014-01-10
forum: General Help
---

### Post by pmcginley on 2014-01-10
i have a 3TB exfat drive mounted in lubuntu 13.10. the drive's label is BACKUP AWAY. when i browse my media folder there are 2 entries, BACKUP AWAY and BACKUP AWAY1. BACKUP AWAY is a broken link to a non-existent drive, while BACKUP AWAY1 is my actual drive. i cannot remove or unmount the incorrect entry (BACKUP AWAY) and i cannot unmount or rename the actual drive (BACKUP AWAY1) as any action is met with the error that 'the drive is not mounted' or 'does not appear in fstab'.

how can i remove the incorrect entry and remount the actual drive under it's proper drive label?

thanks!

---

### Post by cincibluer6 on 2014-01-10
It sounds like the comp is either automounting it, or trying to, to the old location.

Have you tried looking at your fstab to see if it is automounted?

```
sudo blkid
sudo gedit /etc/fstab
```

blkid will tell you what drives are available and fstab is what is mounted.

Regardless, maybe unmounting (via terminal, nautilus, or forcefully (pulling it out)) and then deleting the directory in media might help.

---

