---
title: "grub update - what does the difference in grub.cfg mean?"
date: 2015-07-09
forum: General Help
---

### Post by mastablasta on 2015-07-09
I've got this update today and It asked me if I wanted to keep the old grub.cfg or se the new one. I am not sure what the difference means or if I should take the default one? 

I voted to keep the current one, as I have software RAID1 setup and it seems changes refer to mdadm package?
attached - differences between old and new as presented by the updater.

---

### Post by dino99 on 2015-07-09
Glancing at the changelog let you know better about the diffs; not the latest change, but the last one about mdraid:

grub2 (2.02~beta2-24) unstable; urgency=medium

  [ Mathieu Trudel-Lapierre ]
  * Fix handling of --disk-module option (cherry-pick from fa335308).
    (Closes: #746596, LP: #1309735)
  * Fix double-free of LV names for mdraid (cherry-pick from fc535b32).
    (LP: #1330963)

myself i always choose the default choice, replacing the custom one (but save the actual one in case the upgrade fail with your config)

that diff have already been discussed here [http://ubuntuforums.org/showthread.php?t=2235824](http://ubuntuforums.org/showthread.php?t=2235824)

---

### Post by mastablasta on 2015-07-09
well obviously they were put there upon install for a reason. so I am not sure it's wise to just remove the options.

---

### Post by v3.xx on 2015-07-09
It is my understanding that a grub update will rewrite grub.cfg.  So if you are running a custom grub setup, this will allow you to keep it.

Looks like you made the right choice.

---

