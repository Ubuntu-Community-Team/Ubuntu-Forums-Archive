---
title: "no nautilus scripting support?"
date: 2004-10-27
forum: General Help
---

### Post by rubinstein on 2004-10-27
I can't find the scripts folder. In the documentation it says:
"To view the contents of your scripts folder, choose File-->Scripts-->Open Scripts Folder" but it's not there.
Was scripting removed in Ubuntu?

rubinstein

---

### Post by iwasbiggs on 2004-10-27
I agree, the folder should be more visible, or at least taken out of the documentation so as to not confuse people.

The directory used is actually
~/.gnome2/nautilus-scripts

and after placing one script in there, you will see the menu item become available as well as a script submenu in your context menus.

---

### Post by pocket on 2004-10-27
For newbies like me:
Copy your script to the folder mentioned by rubinstein above.
Right click on your new script and select 'properties'
click the permissions tab
check the "owner: execute" box 

Otherwise, no matter how many scripts you put there, it still won't show.  They have to be executable.

---

