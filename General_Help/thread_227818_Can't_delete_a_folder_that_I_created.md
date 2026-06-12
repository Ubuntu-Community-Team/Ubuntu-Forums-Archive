---
title: "Can't delete a folder that I created"
date: 2006-08-02
forum: General Help
---

### Post by Kenneth Cochran on 2006-08-02
I copied a folder from a windows share to my home folder and now I can't delete it. It just says, "Error while deleting. <File Name> cannot be deleted because you do not have permissions to modify its parent folder." 

Here are the steps I've tried:

Pressed <Delete>
Pressed <Ctrl> + <Delete>
Right-clicked and selected "Mo_v_e to Trash". (This moved it to trash but now I can't empty the trash.)

I tried to delete it from a command terminal but I'm unfamiliar with the command to delete a populated folder recursively.

Is it possible the access rights were copied from the windows share along with the files? I've examined the file permissions of the toplevel folder I'm trying to delete and I have full read, write and execute permissions. I haven't look at the subfolders yet.

---

### Post by Zalbor on 2006-08-02
If your windows partitions are mounted with root only permissions, the directory you copied has the same ones. You need to go to a terminal, cd in the directory where the one you want deleted is and (presuming it's called "folder") give a command like
```
sudo rm -R folder
```
"sudo" gives root priviledges to the command, and "-R" deletes sure every file in the directory.

---

### Post by Ramses de Norre on 2006-08-02
Yes, the permissions of the windows partition will be reserved. And did you check the owner? Maybe it's root who has full permissions.

Any way try ```
sudo chown -R `whoami` path_to_folder && chmod -R 755 path_to_folder
``` to give yourself full acces.

---

### Post by Kenneth Cochran on 2006-08-02
Thanks. I found out shortly after posting that while the top folder had full permissions all the subfolders and file were readonly. Unfortunately changing the parent folder's permissions doesn't appear to propagate to its children.

Thanks again for the quick response.

---

### Post by Lunar_Lamp on 2006-08-02
I often get problems with not being able to empty my wastebasket because there is a file/folder in there with the wrong access permissions.  I can never remember what the path to the wastebasket is either (for manual emptying).

---

### Post by Ramses de Norre on 2006-08-02
~/.Trash, it's simply a hidden folder called Trash in your home folder. 
Not too hard to remember;)

---

### Post by Kenneth Cochran on 2006-08-03
Looks like a feature to set permissions recursively was slated for Nautilus 2.14 but was delayed.

---

