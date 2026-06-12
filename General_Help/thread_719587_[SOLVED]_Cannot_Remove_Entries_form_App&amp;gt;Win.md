---
title: "[SOLVED] Cannot Remove Entries form App&amp;gt;Wine&amp;gt;Programs"
date: 2008-03-09
forum: General Help
---

### Post by Anthony M on 2008-03-09
I have several old programs I installed under Wine that I have since removed, but the folders still show up under Applications>Wine>Programs.

I have tried "Edit Menu" but it will Not remove these entries....

Isnt there a configuration file of the menu list somewhere that I can manually edit to remove these?

Thanks!

---

### Post by disturbedite on 2008-03-09
i've had this problem with numerous versions of wine & kde3.  (not sure about kde4).

if you're on kde...

the only solution i found was to manually edit the kmenu config file here:
/home/username/.config/menus/applications-kmenuedit.menu.

be very careful tho, that file can get quite messy over time & if you delete something by accident, you can mess up the menu.  not too bad tho, the worst think i did was revert the menu to a prior state with a bunch of apps i had unistalled showing back up.

---

### Post by Anthony M on 2008-03-09
> **disturbedite said:**
> i've had this problem with numerous versions of wine & kde3.  (not sure about kde4).

if you're on kde...

the only solution i found was to manually edit the kmenu config file here:
/home/username/.config/menus/applications-kmenuedit.menu.

be very careful tho, that file can get quite messy over time & if you delete something by accident, you can mess up the menu.  not too bad tho, the worst think i did was revert the menu to a prior state with a bunch of apps i had unistalled showing back up.

Thanks! I was able to delete the old entries from /home/username/.config/menus/applications-merged

---

### Post by disturbedite on 2008-03-10
> **Anthony M said:**
> Thanks! I was able to delete the old entries from /home/username/.config/menus/applications-merged
cool, glad to help.
i screwed up my menu several times when i initially tried it, even though i was being very careful.
they (the kde team) really need to devise a new method for the kmenu.  it gets extremely messy over time & hard to decipher.

---

