---
title: "gutsy gibbon to hardy heron"
date: 2008-07-03
forum: General Help
---

### Post by uselessname on 2008-07-03
..guys..i have my 7.10 version and do i still need to back-up my files when i upgarde to 8.04?? or i'll just click the upgrade from the system updater???

tnx...

---

### Post by AnarkistNZ on 2008-07-03
You don't necessarily need to backup anything when running a dist-upgrade.

If however, you run any software that you've changed the configuration in from default (e.g. postfix/apache) it may ask whether you want to keep the existing config, replace it with the new one or compare the differences.

Apart from that, you shouldn't run into any issues.

---

### Post by iaculallad on 2008-07-03
> **uselessname said:**
> ..guys..i have my 7.10 version and do i still need to back-up my files when i upgarde to 8.04?? or i'll just click the upgrade from the system updater???

tnx...

No need to backup your files when performing your upgrade using system updater. It's only your system files that will be upgraded thus leaving your current settings and "some" configuration unchanged.

BTW: If you're "better-to-be-sure" guy, perform your backup now then try to update.

---

### Post by kostkon on 2008-07-03
Just to be sure backup your files, of course! In most cases an upgrade goes well, but you never know. Be sure to backup everything. You can even backup your whole system or make an image of it. Just search these forums for an how-to.

In my case, I upgraded to 7.10 from 7.04 and then to 8.04 and everything went smoothly.

The only point to be careful is that at the end of the upgrade process will ask you if you want to remove the obsolete packages that are not needed in the new version. Be sure to check what is removed and if you are not sure then select to keep them. You will be able to remove them later by doing
```
sudo apt-get autoremove
```

Good luck!

---

