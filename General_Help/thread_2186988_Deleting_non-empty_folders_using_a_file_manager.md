---
title: "Deleting non-empty folders using a file manager"
date: 2013-11-10
forum: General Help
---

### Post by vasa1 on 2013-11-10
I like to delete **~/.thumbnails** periodically. Using a file manager, say Thunar, I can just highlight the .thumbnails folder and press **delete** to send the folder *and* its subfolders to Trash.

What is the "behind-the-scenes" command that is executed by pressing **delete** in the file manager when a non-empty folder is selected?

---

### Post by ajgreeny on 2013-11-10
It will probably be something like ```
mv path/to/foldername/ .local/share/Trash/files/
```
That certainly works as I've just tried it.

---

### Post by vasa1 on 2013-11-10
> **ajgreeny said:**
> It will probably be something like ```
mv path/to/foldername/ .local/share/Trash/files/
```
That certainly works as I've just tried it.
There maybe a little more going on ...
 .local/share/Trash/ has files/, expunged/, and info/. Deleting via the file manager certainly gets the deleted material into files/ but info/ is also modified.

---

### Post by steeldriver on 2013-11-10
Under gnome, it's gvfs-trash I think

```

$ gvfs-trash --help
Usage:
  gvfs-trash [OPTION...] - move files to trash

```

---

### Post by ajgreeny on 2013-11-10
I have just noticed that any files or folders moved to trash as suggested in my last post can not be restored using thunar or nautilus as the path can not be found by the system, so you need to proceed with some caution if you have used my command.

---

