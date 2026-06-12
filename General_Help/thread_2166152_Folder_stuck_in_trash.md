---
title: "Folder stuck in trash"
date: 2013-08-08
forum: General Help
---

### Post by kohls2 on 2013-08-08
Not sure how it got in there, but there is a folder labeled wicd in the trash. It cannot be deleted or removed. If I hit "empty trash" the folder stays there. If I try to drag it out of the trash, I get a warning that I don't have permission to do so. The original item stays in the trash and a copy appears on the desktop where I tried to drag it. If I right-click there is no option to restore it to its original position.

---

### Post by deadflowr on 2013-08-08
You probably deleted that with root privileges.
Look in /home/user/.local/share/Trash.
That's where that file should be.
then try running sudo rm -rf the full path to that file.
or simply try changing the ownership to you
```
sudo chown you:you the-path-to-the-file
```
Then delete it.

---

### Post by kohls2 on 2013-08-09
Thank you!

---

