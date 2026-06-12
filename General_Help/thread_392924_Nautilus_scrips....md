---
title: "Nautilus scrips..."
date: 2007-03-25
forum: General Help
---

### Post by Andruk Tatum on 2007-03-25
I was thinking the other day, in nautilus, you have to "root here" to open up another nautilus to rename (or whatever) a file.

Wouldn't it be possible that instead of having to "sudo nautilus", nautilus could just 1) see if the user has the rights to open/edit/rename/execute a file and if the user does not have permissions, 2) use the normal "rename" or "Open in Text Editor" options to popup gksudo to run gedit or whatever to open the file?

Theoretically, this should be able to be done with a few if statements.

---

### Post by zvacet on 2007-03-25
Install nautilus scripts with Automatix.

---

### Post by Andruk Tatum on 2007-03-27
Right, and those work fine, it's just that I think that would have been a great feature to have developed for nautilus, and instead of having to use scripts that (i would say) most users may not know, simply have the program check to see if it "needs" root access and automatically ask for it.

Sorry if this is in the wrong forum.

---

### Post by CocoAUS on 2007-03-27
I definitely agree that the functionality should be built right in.  It's not impossible to do it via the command line every time, but it's an absolute pain in the butt--one we shouldn't have to bother with.  But yeah, it probably won't do any good to post it here.  Perhaps the Gnome bugzilla?

---

### Post by STREETURCHINE on 2007-03-27
create a root launcher

click on desktop,click create a launcher.

type: application
name: root
command: gksudo "gnome-open %u"

click ok

right click .>properties>
click on the no icon then choose your icon for it,it will show up on your desktop,

then all you have to do is drag the file to the desktop icon and it will open in root ,same as the script just a bit quicker...

---

### Post by zvacet on 2007-03-27
Right click on file/folder and you will see nautilus scripts.pick one you need and that is it.

---

