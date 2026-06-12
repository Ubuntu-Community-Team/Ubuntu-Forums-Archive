---
title: "Folder Redirection"
date: 2020-02-27
forum: General Help
---

### Post by uthall on 2020-02-27
Hello

I have an application that writes data to FolderA.

I have now installed new disks with more capacity, and what the application to now write to FolderB

However, there is no way in the application to point it to folderB.

Is there some type of redirection that can be used?

---

### Post by HermanAB on 2020-02-27
You can make a soft link to a folder with the ln -s command.
[https://www.tecmint.com/create-hard-and-symbolic-links-in-linux/](https://www.tecmint.com/create-hard-and-symbolic-links-in-linux/)

---

### Post by uthall on 2020-02-27
Thanks, but will a sylink make sure data is copied to the new folder and not the old one?

---

### Post by freebird54 on 2020-02-28
After a symlink (soft link) is created, only a redirect exists by that name in the original location. All file interactions actually occur in the new destination location.
For example, I ran with ALL the normal data directories (Documents, Downloads, Music, Pictures,Videos etc) soft linked to a different drive. This makes it really easy to back up the data, and makes it accessible immediately from any distro (live or not) running on the system. Just remember to rename or remove (when empty) any directory (folder) you plan to redirect before linking it.

Freebird54

---

### Post by The Cog on 2020-02-28
Firstly, move the original folder to its new location on the new drive. Now the data is where you want it to be, and no trace exists in the original location. Make a copy first if you want to.
Then create a symlink, located where the old folder was, pointing to the new folder. e.g.
```

# Optional make a copy of the data first
cp oldplace/myfolder oldplace/myfolder-backup
# Move myfolder to its new home
mv oldplace/myfolder newplace/myfolder
# Make a symlink where the app expects to find the folder, pointing to the new place
ln -s newplace/myfolder oldplace/myfolder
```

---

### Post by vanadium on 2020-02-28
Symlinks will do it here, and are the most simple approach. You can, however, achieve this at a deeper level in the system with a "mount bind". This mounts the new folder onto a folder.

---

