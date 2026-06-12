---
title: "How do I delete a Launcher Icon and related Files"
date: 2012-11-11
forum: General Help
---

### Post by alligoodw on 2012-11-11
Using Ubuntu 12.10 and looking through the application lens, I've noted a few icons that should be deleted - they don't work properly as they're something I created myself. I need to delete those icons and their associated files but I don't know how. How do I delete those bad icons?

---

### Post by Frogs Hair on 2012-11-11
Start with the directory that you placed the icons in when you created them. I place my home made icons in an icons folder in pictures.

If the icons are appearing in Dash even though you have deleted them open the privacy application > recent items and delete history. You may have to log out/in for the changes to take effect.

---

### Post by alligoodw on 2012-11-11
> **Frogs Hair said:**
> Start with the directory that you placed the icons in when you created them. I place my home made icons in an icons folder in pictures.

If the icons are appearing in Dash even though you have deleted them open the privacy application > recent items and delete history. You may have to log out/in for the changes to take effect.

I guess what I'm asking is where are the icons located within the File System? As root, I'll delete them from there.

---

### Post by Frogs Hair on 2012-11-11
The location in in the root file system is usr/share/icons. The custom icons would only be there if you put them there.

---

### Post by efflandt on 2012-11-11
You said that you created the icons, but not how or where, which should give you a clue where to remove them from.

You might be confusing icons with launchers.  Icons you see in Dash, other than recently accessed or downloaded files, are typically desktop launchers that have an icon associated with them.  The launchers are in **/usr/share/applications** owned by root.

If you installed **MainMenu** (alacarte) to make the launchers, maybe you could use that to delete them.  You do not really want to remove system icons if one of the standard icons was used for your launchers.

---

### Post by alligoodw on 2012-11-11
This answered my question and resolved my issue. I found the icons I was looking for and removed them promptly. The correct icon still remains. I appreciate the replies and your time.  I bid you good day.

---

