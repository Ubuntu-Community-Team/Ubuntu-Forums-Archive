---
title: "Deja Dup backup Ubuntu 18.04"
date: 2019-07-09
forum: General Help
---

### Post by Robbyx on 2019-07-09
Has anyone a way of pruning the Duplicity backup files so that I just have

The last 11 month end full back ups
Last 3  weekly full backups
Last 7 daily incremental backups from the last full backup 

Also I could not find the config file for Deja dup/ Duplicity. Where is it stored? I ask in case there is something in the config files that limit the amount of backups that accumulate, but more in line with the above than just reducing the size of the partition.

---

### Post by CatKiller on 2019-07-09
Déjà Dup has no mechanism for removing old backups. The duplicity command-line utility can go through your backups and remove all but *n* backups, though.

---

### Post by #&amp;thj^% on 2019-07-09
Along with CatKiller's advice:
Deja-dup does not yet supply a way of removing old backups, you should not delete some of the files, that  might leave your backups without a start file and render them invalid.
Also worth noting, You can use the Dconf editor to modify setting at path org.gnome.DejaDup, key name delete-after. It's set to the number of days to keep backup files on backup location.

Or from terminal. to set it to 60 days from the command line, run example:
```

gsettings set org.gnome.DejaDup delete-after 60
```

---

### Post by Robbyx on 2019-07-09
Thank you both for your guidance. Have you any views on how many days to keep. As a corruption can be carried forward until the original is lost I always used to use the grandfather, father, son approach, but not now with Deja dup.

---

### Post by #&amp;thj^% on 2019-07-09
I use 90 days, but I also back that up to another storage device, and start a-new as needed (While still having the original back-up).
And I use DD (not "Deja Dup") for my back-up's (I had to make that clear) opening the "Backups" GUI will sometimes cause this setting to revert to "At least 6 months" when the app is closed again.(So a heads-up if you will)
I can only guess our back-up needs are different though.

---

