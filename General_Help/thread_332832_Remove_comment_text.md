---
title: "Remove comment text??"
date: 2007-01-06
forum: General Help
---

### Post by ChristopherL on 2007-01-06
How do I remove the comment texts from ex. power button icon , date/clock icon, menu etc.

---

### Post by 23meg on 2007-01-06
Do you mean the mouseover tooltips?

---

### Post by ChristopherL on 2007-01-07
yes

---

### Post by mcduck on 2007-01-07
Open Configuration Editor (Alt-F2 and run 'gconf-editor', browse to /apps/panel/global and disable 'tooltips_enabled' :)

(you might need to 'killall gnome-panel' after changing the setting)

---

### Post by angkor on 2007-01-20
> **mcduck said:**
> Open Configuration Editor (Alt-F2 and run 'gconf-editor', browse to /apps/panel/global and disable 'tooltips_enabled' :)

(you might need to 'killall gnome-panel' after changing the setting)

That only works for things in the menus, but not for the windows list, notification area or the desktop switcher. Anyone know how to disable all tooltips?

---

### Post by albesan on 2007-01-30
Yes, how do you disable tooltips on both panels at least?
I have been looking at gconf but can't seem to find an entry other than the one I used to disable the tooltips on the top panel.

any ideas?

a.

---

### Post by justaguynpc on 2007-02-01
Double check to see that you have it installed, if not, install, then using the command line ¨conf-editor" will get you where you want to be.

---

