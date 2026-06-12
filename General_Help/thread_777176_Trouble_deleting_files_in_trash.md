---
title: "Trouble deleting files in trash"
date: 2008-05-01
forum: General Help
---

### Post by notesetter on 2008-05-01
I've migrated some thunderbird folders over from win xp to ubuntu studio 8.04 and to make a long story short, some of them are now in my trash bin. When I try to empty trash, the folder goes through its file operations but the files are still there. If I try to delete the folders individually, I get a message: "error removing file: permission denied"

I've changed all of the permissions on the folders to allow read/write and to create/delete files and applied the changes to subfolders and files--still no luck.

I've even tried sudo rm from a terminal and got "rm: cannot remove '6zdpufab.default': Is a directory"

Any thoughts or suggestions?

Thanks,

Dave

---

### Post by cb951303 on 2008-05-01
```
sudo rm -R /home/$userName/.local/share/Trash
```

---

