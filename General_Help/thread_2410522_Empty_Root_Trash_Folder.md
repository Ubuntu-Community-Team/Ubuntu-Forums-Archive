---
title: "Empty Root Trash Folder"
date: 2019-01-16
forum: General Help
---

### Post by Redalien0304 on 2019-01-16
Would like to Empty my Root/.local/share/Trash both the "files & info" Folders.
I am using Cinnamon DE with Nemo File Manager. Have tried using  through sudo  but no Luck?

---

### Post by Tadaen_Sylvermane on 2019-01-16
From a terminal enter this to become root

```
sudo -i
```

Then navigate to the path via the command line

```
cd /root/.local/share/Trash
```

Then remove the offending files manually

```
rm -r "$FILENAME"
```

This is one of many cases where the GUI makes it harder, not easier. Be very sure about what you type while logged in with root. You can destroy your system in about 1 second if not careful. Is why it is almost never recommended.

I'm curious how this was created as you would need GUI access as root for that to even be created I think.

---

### Post by Redalien0304 on 2019-01-17
Ok thanks worked Perfectly & no Problems.

---

