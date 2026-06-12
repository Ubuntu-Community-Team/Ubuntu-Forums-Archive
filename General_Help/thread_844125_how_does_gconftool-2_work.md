---
title: "how does gconftool-2 work ?"
date: 2008-06-29
forum: General Help
---

### Post by dexter.deepak on 2008-06-29
i have frequently used the commands like:
 gconftool-2 --get /desktop/gnome/background/picture_filename
or 
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'

but i unable to find the location of the files to be passed as an argument, like:
/apps/nautilus/desktop....or /desktop/gnome/....

this way i am unable to utilize this command  properly.
does anyone try finding that "which" location is to be passed as an argument ?

---

### Post by nick_h on 2008-06-29
If you run the gconf-editor manually then you can browse through the keys.

```
gconf-editor
```

Or you can enable it on your menu under Applications->System Tools (right-click on "Applications" then select "Edit Menus")

---

### Post by lswb on 2008-06-29
It is confusing if you are expecting actual files, but the gconf tool uses the / character to designate branches in the configuration key database heirarchy. The arguments to gconftool are not actual file names, but are used to locate a specific key in the gconf database. Conceptually it is somewhat like a filesystem, with directories and subdirectories but these keys are all stored in a single database, not separate files.

---

