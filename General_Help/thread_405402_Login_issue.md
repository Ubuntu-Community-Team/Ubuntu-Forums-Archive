---
title: "Login issue"
date: 2007-04-09
forum: General Help
---

### Post by Leebo on 2007-04-09
Hello all,

I am having probs loggin into ubuntu. Everything was wiorking fine a few days ago, but i was leaving town and i left the desktop off for a couple of days. When i turned computer back on, everything went fine when i went to login to gnome, it logs in and starts loading everything...then it goes to black screen then back to login screen.

 It does this for gnome, failsafe gnome and for xfce it actually logs in for a few seconds, but then it logs back out. I already went into terminal and did upgrade but still no change.

I am using Edgy w/ Beryl

Any info would be appreciated so that i can get out of this craooy windows environment :) .

Thanks in advanced!

Leebo

---

### Post by taurus on 2007-04-09
Boot into recovery mode from GRUB menu and post the output of this command here.

```
df -h
```

---

### Post by Leebo on 2007-04-09
Here is output:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              47G   24G   22G  52% /
varrun                252M  132K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb             10M  124K  9.9M   2% /proc/bus/usb
udev                   10M  124K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M  8.0M  244M   4% /lib/modules/2.6.17-11-generic/volatile
/dev/hda1              62G   26G   36G  42% /media/hda1

```

---

### Post by Leebo on 2007-04-09
well got logged back in finally...when i could log in as another user i created that wasnt using beryl, i figured berly was the problem...so i uninstalled...and all is working again

thanks for the help neways :)

Leebo

---

