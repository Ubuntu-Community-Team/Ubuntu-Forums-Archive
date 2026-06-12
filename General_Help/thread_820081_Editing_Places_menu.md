---
title: "Editing Places menu"
date: 2008-06-05
forum: General Help
---

### Post by casualfanta on 2008-06-05
Despite some fairly extensive searches I haven't worked out a way to stop my windows and extra partitions (Dell recovery and mediadirect partitions) from appearing on my places menu.  They aren't causing a problem as such, but since i do not intend to mount said partitions, I would prefer that they weren't cluttering up my Places menu.
So in summary - is there a way to customise the items that appear on the Places menu.

I would also like to have all 6 of my bookmarks appear on the main Places menu rather than in their own separate folder - is there a way to change this too.

Cheers

---

### Post by casualfanta on 2008-06-09
bump

---

### Post by prshah on 2008-06-10
> **casualfanta said:**
> stop my windows and extra partitions (Dell recovery and mediadirect partitions) from appearing on my places menu.  


You can edit your /etc/fstab and comment out the "said" partition(s). For more details, post the outputs of the following commands```

cat /etc/fstab
sudo fdisk -l
```

---

### Post by Forlong on 2008-06-10
Instead of commenting them out, you should mount the partitions you don't want to show up there from /media to /mnt by default.

---

### Post by iv2101 on 2008-07-24
I have a similar question: how to remove/add items to the PLACES menu? it is trivial to modify the APPLICATIONS menu, but I can't even locate the settings file for PLACES.
Thanks!

---

### Post by prshah on 2008-07-24
> **iv2101 said:**
> I have a similar question: how to remove/add items to the PLACES menu? it is trivial to modify the APPLICATIONS menu, but I can't even locate the settings file for PLACES.
Thanks!

From any "Open" dialog box, you can drag-n-drop folders to add to the places menu... I assume the reverse will remove.

---

### Post by iv2101 on 2008-07-28
> **prshah said:**
> From any "Open" dialog box, you can drag-n-drop folders to add to the places menu... I assume the reverse will remove.

This only creates duplicates of the items in the menu. Thanks for the advice though. I certainly want to delete some of the things there.

---

### Post by iv2101 on 2008-08-09
bump 

how do i ADD/REMOVE items to/from the places menu?

---

### Post by DaymItzJack on 2008-08-10
[[IMG]http://img291.imageshack.us/img291/8029/screenshotlz0.th.png[/IMG]](http://img291.imageshack.us/my.php?image=screenshotlz0.png)

---

### Post by iv2101 on 2008-08-10
Thanks! my side panel was always hidden so i didn't notice this

---

### Post by jelly on 2008-08-28
Awesome, thanks DaymItzJack - I've been looking for a way to edit the Places menu for a while now.

- Jelly.

---

### Post by majoob on 2010-11-11
How do you remove an item from Places? "Remove" is disabled in my menu (see screenshot). "backup" is the name of my external backup drive. Each time I unmount/mount, it just adds another "backup" to Places, cluttering it up. The top one is the icon for the actual mounted drive. I'd like to remove the bottom two.
[IMG]http://picasaweb.google.com/matt.oberle/Screenshot?authkey=Gv1sRgCIyX5tWDrej5VA#5538426950622888466[/IMG]

---

