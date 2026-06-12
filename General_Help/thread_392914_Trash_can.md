---
title: "Trash can"
date: 2007-03-25
forum: General Help
---

### Post by crabhunter on 2007-03-25
I have just cleaned up my desktop ubuntu6.10 and didn't realize I had selected the trash can as well!
Of course now I need one of the files.
Can I get it back? where is trash in the file system?
Mike

---

### Post by mcduck on 2007-03-25
All your removed files go to hidden directory inside your home dir, called .Trash. hit alt-h in file browser to see it.

I didn't quite understand if you mean that you emptied the trash can (which means that your files are now gone) or that you had a shortcut to your trash can on your desktop (there's a better way to get a trash icon on the desktop)..

---

### Post by Gannin on 2007-03-25
Your trash should be in ~/.Trash.  You can get the icon back by right-clicking on a panel, choosing "Add to Panel", then choosing the Trash icon.  At that point you can either leave it on the panel, or drag it onto the desktop.

---

### Post by mcduck on 2007-03-25
> **Gannin said:**
> Your trash should be in ~/.Trash.  You can get the icon back by right-clicking on a panel, choosing "Add to Panel", then choosing the Trash icon.  At that point you can either leave it on the panel, or drag it onto the desktop.

For trash icon in desktop it's better yo use the built-in icon that you can enable through Configuration Editor. That icon cannot be accidentally deleted, and it also follows your icon theme automatically:

1. Hit Alt-F2 and run 'gconf-editor'
2. browse to apps/nautilus/desktop
3. enable 'trash_icon_visible'

---

