---
title: "How do I edit a links target"
date: 2008-06-06
forum: General Help
---

### Post by ChaosMastero on 2008-06-06
How do I edit a link\shortcut's target?

---

### Post by nick_h on 2008-06-06
For a desktop launcher right-click on it and select properties.  You can then edit then command in the launcher tab.

For a symbolic link you will have to delete it and create a new one.

---

### Post by ibuclaw on 2008-06-06
Symbolics links can be created and editted in the Terminal

To create one, use the command "**ln -s**" (that is L, not 1):
```
ln -s /path/to/file /path/to/symlink
```
To change where the symlink points to, append the force ("**-f**") option to remove the already existing one.
```
ln -fs /path/to/file2 /path/to/symlink
```
Typing in "**ls -l symlink**" (symlink is the name of the link) in the directory where the symlink is will show you the change.
BEFORE:
```
lrwxrwxrwx 1 name name 4 2008-06-06 20:00 symlink -> /path/to/file
```
AFTER:
```
lrwxrwxrwx 1 name name 4 2008-06-06 20:00 symlink -> /path/to/file2
```

Regards
Iain

---

