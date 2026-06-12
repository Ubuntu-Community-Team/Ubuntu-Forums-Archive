---
title: "Appalled: Why can't I add &quot;Computer&quot; to panel???"
date: 2007-04-22
forum: General Help
---

### Post by casperlingus on 2007-04-22
It is ludicrous to me that it's so difficult to add a "Computer"  or "Home Folder" icon on the top panel.  I'm sure I could figure out the nautilus command to do that and add a custom icon, but why should I need to do that?

Am I being retarded?  Am I missing something obvious?   "Places" is the only menu where you can't right click and select "Add to panel".  And I can't find it anywhere under the "Add to panel..." dialog after right clicking the panel.

I've been using Ubuntu for 2 years and just did a fresh Feisty install.  I'm appalled that this hasn't been "fixed" yet...?  Someone please tell me I'm missing something stupid.

-Casper

---

### Post by SunnyRabbiera on 2007-04-22
Its actually easy to do, I have done it myself.
what you need to do is use the configuration editor (it is hidden initially in the menu, right click on the main menu (Applications Places System) and use the menu editor, alternately you can go to system then to "preferences" then click on "main menu")
once the menu editor is up click on "system tools"
then put a checkmark next to the program called "configuration editor" by clicking on the box next to it.
from there you can now acess the configuration editor in your menu.
close the menu editor
then go to "applications" then to "system tools" then start up the configuation editor.
once it is open click on the little arrow next to "apps"
your list will be expanded now
move down to "nautilus"
click on the arrow next to it
then select "desktop"
here you have some boxes, make your computer icon visible by clicking on the box next to "computer icon visible"
select any others that might be useful like a desktop link to your home folder, doccuments and et cetra.
after making your changes exit the configuration editor.
now just drag and drop your newfound computer icon to your panel and boom you got a link to your computer in your panel.

---

### Post by chrisccoulson on 2007-04-22
I created custom launchers containing the following commands on my panels:

```
nautilus --no-desktop computer:///
nautilus --no-desktop $HOME
```

I've also added others like

```
nautilus --no-desktop burn:///
nautilus --no-desktop /
```

---

### Post by Ziggy72 on 2007-04-22
It's really very, very easy. For any of the Application, Places and System menu items, all you need to do is a **[COLOR="Red"]left click  drag and drop[/COLOR]** on any application in the drop down menus. This will copy the launcher to wherever you want - Desktop, folder, panel....

---

### Post by casperlingus on 2007-04-22
Okay, so the left-click-and-drag worked.  Glad I finally got that out of the way.

But no one has answered my question yet...why is it so hard to do this/figure this out?  If you didn't notice, the first two answers were not the simplest, and even this solution isn't obvious.  For me it was the first thing I wanted to do when I did a fresh install, is this not the case for other people?  I could see this being pretty frustrating for a new user.  

Why can't we add "Computer" and "Home Folder" to the list of things in the "Add to panel..." dialog and/or make it possible to right-click in the "Places" menu like you can in the other menu?

-Casper

---

### Post by ramjet_1953 on 2007-04-23
Click System>About Gnome

A browser window opens and you can navigate to the GNOME documentation, which gives full details on the use of the GNOME desktop.

Sure, we can help you with your questions, but you need to understand that everyone here is offering help voluntarily.

Whinging doesn't really get you anywhere.

Regards,
Roger

---

### Post by Mr Gav on 2007-04-23
Thanks Sunny,

Just the trick!

g

---

