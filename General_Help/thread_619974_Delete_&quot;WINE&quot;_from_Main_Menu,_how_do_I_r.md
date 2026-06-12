---
title: "Delete &quot;WINE&quot; from Main Menu, how do I re-add?"
date: 2007-11-22
forum: General Help
---

### Post by cisforcojo on 2007-11-22
I'm reinstalling wine and deleted it from my Main Menu since

```
sudo apt-get remove --purge wine
```

didn't do the job. Now that I've reinstalled wine, I had to manually re-add 'Wine" to my Main Menu but when I install apps with Wine, they're not adding to my Gnome menu. What's up?

---

### Post by MrFSL on 2007-11-22
First remove wine:
```
sudo apt-get --purge remove wine
```
Next remove the wine menu folder:
```
sudo rm -r /home/username/.config/menus
```
There has been a lot of hub-bub about people giving bad advice intentionally when using the *rm -r* commands. Please inspect the contents of this folder first to make sure you are deleting what you think you are deleting.

Restart gnome-panel
```
killall gnome-panel
```

(The wine entries should be gone) Now reinstall wine.

---

### Post by cisforcojo on 2007-11-22
Hmm... Thanks but WINE still isn't adding apps to the GNOME menu under 'Wine" (or at all)
Do you know what could be causing this? (I'm installing Microsoft Office 2003 and it's currently not adding anything. It's not terribly important, just takes care of some tedious setup. Thanks!

EDIT: Nevermind! Just needed a little time to show up on the menu. Thanks!

---

### Post by urosh2 on 2008-03-16
Thank you for this. It helped me.

---

### Post by bwdease on 2008-03-23
Dell-2400.  I deleted the wine icons from the menu as well.  Tried the suggestion mentioned here, and at first it did not work.  But, then I realized my error.  Where it says "username" you need to put your login username.  DUHH!  This really helped me, and it worked.  Thanks for the ground work!!

      :lolflag::lolflag:

---

### Post by Ice_l3lade on 2008-06-10
> **MrFSL said:**
> First remove wine:
```
sudo apt-get --purge remove wine
```
Next remove the wine menu folder:
```
sudo rm -r /home/username/.config/menus
```
There has been a lot of hub-bub about people giving bad advice intentionally when using the *rm -r* commands. Please inspect the contents of this folder first to make sure you are deleting what you think you are deleting.

Restart gnome-panel
```
killall gnome-panel
```

(The wine entries should be gone) Now reinstall wine.
Uninstalling wine is not really necessary. Just removing the .config/menus and restarting gnome-panel is enough to have wine recreate it's menus.
(At least, that worked here)

Thank you for this topic :)

---

### Post by MrFSL on 2008-06-10
Your absolutely correct - but the original poster had said:

> ...I'm reinstalling wine...

So - geared for that scenario.

Greets!
MrFSL

---

### Post by chelarnens on 2008-06-14
An even easier way is to remove the "<Deleted>" entry under "<Name>wine-wine</Name>" in :~/.config/menus/applications.menu

---

