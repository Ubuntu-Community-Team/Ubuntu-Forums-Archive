---
title: "Folder permissions"
date: 2008-06-27
forum: General Help
---

### Post by notlim_hardy on 2008-06-27
Halo. I created a folder in order to copy a plugin file, but I can't copy anything to this new folder, guess I can only do that as root. Is there a way to set it so I can copy files to there by the gnome file manager? Tankan.

---

### Post by tamoneya on 2008-06-27
it is probably because the owner of the directory is root.  Try this: ```
sudo chown -R username /path/to/directory
```
If for some reason that doesnt work please post the results of:```
ls -l /path/to/directory/..
ls -l /path/to/directory/
```

---

