---
title: "Help with WINE - nooby"
date: 2008-03-14
forum: General Help
---

### Post by Leo the Lion on 2008-03-14
I'm sorry if this has been answered before, but I wasn't able to find it.
I think I royally screwed with WINE. I installed a software under WINE, but when I tried to uninstall it using the sofware's own "uninstall" icon it didn't go through. I got frustrated and deleted everything manually (yes, I know it was stupid). Now the software still shows up under the WINE drop down menu and I'm not sure how to remove it. 
Any ideas on how to revert this rather stupid mistake.

Thanks a bunch.

---

### Post by SPr on 2008-03-14
[http://ubuntuforums.org/showthread.php?t=35331](http://ubuntuforums.org/showthread.php?t=35331) Here you go :)

---

### Post by Leo the Lion on 2008-03-14
Yeah, I tried "ls /usr/share/applications/ ", but still can't see the application to delete it.

---

### Post by mc4man on 2008-03-14
If you just want to remove the entry from the wine drop down right click applications>edit menus - expand the wine tree on left to programs and uncheck or if you want delete the entry in question
the actual program menu would be in /home/<username>/.config/menus/applications-merged

---

### Post by Leo the Lion on 2008-03-14
> **mc4man said:**
> If you just want to remove the entry from the wine drop down right click applications>edit menus - expand the wine tree on left to programs and uncheck or if you want delete the entry in question
the actual program menu would be in /home/<username>/.config/menus/applications-merged

Cool, got the entry out of the WINE drop down. Now if I want to delete it, how do I go about doing it? Sorry for the noob question.

---

### Post by mc4man on 2008-03-14
When you unchecked it in edit menus you could have (and still can ) right clicked on the entry (the one you just unchecked)  and chosen delete
If you really want to delete the actual menu itself follow path as above - it's not doing any harm - I'd leave it. Note -  if you must -  .config is a hidden file in home directory - places>home/<username> - then use ctrl h key combo to show hidden files

---

### Post by Leo the Lion on 2008-03-14
> **mc4man said:**
> When you unchecked it in edit menus you could have (and still can ) right clicked on the entry (the one you just unchecked)  and chosen delete
If you really want to delete the actual menu itself follow path as above - it's not doing any harm - I'd leave it. Note -  if you must -  .config is a hidden file in home directory - places>home/<username> - then use ctrl h key combo to show hidden files
Thanks a bunch!!

---

