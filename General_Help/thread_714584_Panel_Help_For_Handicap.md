---
title: "Panel Help For Handicap"
date: 2008-03-03
forum: General Help
---

### Post by bmac on 2008-03-03
My niece has a mental handicap and has trouble with panels in Ubuntu 7.1 (Gusty). For obvious reasons she doesn't understand how the panels are utilized. Her desktop consists of a single panel which can't be deleted just by right clicking on the panel until another panel is installed then either panel can be deleted by the simple right click. The problem is she will add a panel then inadvertently delete the main panel which requires myself or her dad to either rebuild the panel or reload it from backup. 
My question is can someone help figure a way to make adding or deleting panels an administration task which would require an administrative password to perform, at least on her desktop? She really loves Ubuntu and has found it significantly more user friendly than any Windows OS. She enjoys the freedom of desktop manipulation and of course gets help from the family members. We all run Ubuntu and except for some issues with video cards have found the platform to be extremely stable and functional.
Thanks
BMac

---

### Post by neilengineer on 2008-03-04
Better create her own account in Ubuntu and use it.  So if she messed things up, just delete her account and recreate it.  

Or maybe just delete the .gconf in /home/username will do the trick.

---

### Post by Technophobia on 2008-03-04
Try this

Alt+F2 To bring up the Run Application Dialog.

Enter- **gconf-editor**

Navigate to **/apps/panel/global**

scroll down to **locked_down**

click the check box and your done.

---

### Post by bmac on 2008-03-04
I actually found the solution. If anyone else needs to protect their panels.   Open system tools/configuration editor Left click the triangle next to Apps Left click Panel triangle  Left click on global On the right window left click on the Locked_Down check box   This viturally locks the panel and will not allow for panel or applet deletion.

---

### Post by talsemgeest on 2008-03-04
There will be an easy way to do it with a password when hardy comes out

---

