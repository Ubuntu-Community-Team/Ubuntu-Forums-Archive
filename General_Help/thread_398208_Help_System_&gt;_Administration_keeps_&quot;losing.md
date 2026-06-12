---
title: "Help: System &gt; Administration keeps &quot;losing&quot; programs"
date: 2007-03-31
forum: General Help
---

### Post by tj.milligan on 2007-03-31
**Background**
Since the days of RedHat 7.2 I've been using KDE; however, I've come to prefer the spartan look of GNOME, so here I am [using Ubuntu]. With KDE, I've never had problems editing the start (K) menu, but I've never had anything BUT problems trying to edit GNOME menus.

**Problem**
Even Ubuntu's default GNOME menu is bloated. For instance, Evolution shows up under Applications > Office and Applications > Internet. :confused:  I don't have an HP printer, so I want to remove the entry System > Preferences > HP toolbox; same goes w/ System > Accessibility and several others. Should be a piece of cake, right? :mad: 

System > Preferences > Main Menu (or System > Preferences > Menu Layout as it's referred to in Edgy), simply doesn't work. I can't check or uncheck any boxes, since it doesn't launch via gksu. So instead I run sudo alacarte. Sometimes this works, most of the time it doesn't (yes, even after killall gnome-panel and/or restarting). And in my latest case, I run sudo alacarte, it SHOWS checks next to all of the System > Administration programs, but only five apps show up in my menu. Originally had 15 to 20 in there, then seven, and 2 more disappeared the last time I used alacarte. BTW, the Applications and System > Preferences show all the applications, just having issue w/ System > Administration.

So, can I bypass this ridiculous frustration and edit some .conf file somewhere? How do I get my "missing" System > Administration programs back (yes, they're installed or symlinked in /usr/bin, the only thing missing is the menu bar shortcut. BTW, I'm having this problem on my Feisty workstation and my Edgy laptop. TIA.

---

### Post by tj.milligan on 2007-03-31
bump

---

### Post by tj.milligan on 2007-03-31
bump

EDIT --

FIXED! Resolution here: [http://ubuntuforums.org/showthread.php?t=400753](http://ubuntuforums.org/showthread.php?t=400753)

---

