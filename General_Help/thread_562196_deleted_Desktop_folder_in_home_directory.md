---
title: "deleted Desktop folder in home directory"
date: 2007-09-28
forum: General Help
---

### Post by surf rock on 2007-09-28
Okay, so last night, while wantonly deleting files and folders in my home directory during a mass clean-up operation, I accidentally deleted the Desktop folder and, consequently, emptied it from Trash not long after. After restarting my computer this morning, it appears that all of the files and folders in my home directory are now showing up on my desktop, and I can't delete anything on my desktop without clearing it from my home directory as well. I assume this has something to do with me removing the Desktop folder from my home directory, so my question is, how can I restore that Desktop folder and get all of these files off my desktop? If it helps, I'm using GNOME. 

Note: I found another topic similar to this, and this is what someone had to say:

> **Lord Illidan said:**
> Make a Desktop folder, then open a terminal and run

```
gconf-editor
```

Once there, navigate to /apps/nautilus/preferences and on the right pane, set desktop_is_home_dir to false.

I made a new Desktop folder, but the desktop_is_home_dir key was already set to false, and yet the files are still showing up on my desktop.

---

### Post by TheExplorer on 2007-09-28
Just create that folder again. The permissions should be drwxr-xr-x i.e: right click on the Desktop folder -> Properties -> Permissions tab and check everything except write permission for Group and Others.

---

### Post by phektus on 2007-10-24
This also happened to me. I ran gconf-editor and set the desktop_is_home_dir variable to false. I also did chmod 755 ~/Desktop to set the folder drwxr-xr-x permissions. Still, my home folder content is showing in my desktop. Anybody here knows how to fix this?

---

### Post by commonlyUNIQU3 on 2007-10-24
I'm assuming that you have created the folder entitled "Desktop" and not "desktop" (case sensitivity!)?

---

### Post by phektus on 2007-10-24
Yeah it's spelled Desktop. In my case, I accidentally moved it to the Templates folder. I tried to copy it back, and then this. I even set the right permissions.

~$ ls -l
total 50124
-rw-r--r-- 1 root  root         0 2007-10-22 18:52 1
drwxr-xr-x 2 arbie arbie     4096 2007-10-22 20:02 bin
drwxr-xr-x 2 arbie arbie     4096 2007-10-24 23:52 Desktop

---

### Post by 23meg on 2007-10-26
This fixed it for me:

[http://ubuntuforums.org/showthread.php?t=581498](http://ubuntuforums.org/showthread.php?t=581498)

---

