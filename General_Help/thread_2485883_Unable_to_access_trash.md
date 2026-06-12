---
title: "Unable to access trash"
date: 2023-04-12
forum: General Help
---

### Post by xanizen on 2023-04-12
This is an issue that intermittently arises. Usually after deleting a 4+ GB file. Sometimes a message will pop up saying the item can't be sent to trash and that it can only be deleted right away. I'm sure the trash isn't full.

The pop up says:
The location could not be displayed.
Sorry, could not display all the contents of "trash:///": Operation not supported

---

### Post by TheFu on 2023-04-14
Trash is located on the same file system as the files being deleted. 
There are 2 different places.
a) If the file(s) are on the same file system as your HOME directory, the .Trash/ will be under your HOME (somewhere).
b) If the file(s) are on a different file system than your HOME directory AND if those file systems don't allow your userid to create the .Trash/ directory  just below the mount point OR if the storage is on the network, then trash won't work.

---

### Post by xanizen on 2023-10-01
I had to execute 'kill nautilus' in the terminal.
This has been happening less frequently though.

---

