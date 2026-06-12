---
title: "Change owner of mounted drive"
date: 2020-11-23
forum: General Help
---

### Post by themeadows94 on 2020-11-23
I just installed 20.04.1. I want to change the owner of two mounted drives from root to [username]. The drives just contain stuff like music, games, video. The goal: I want Steam to be able to use folders on those drives as library folders.

I just tried a GUI route of running Nautilus in sudo then changing permissions within Nautilus (right click on mnt/drive-name and changing permissions there), but I get the error message "The owner could not be changed. Sorry, could not change the owner of "Drive": Error setting owner: Operation not permitted"

How should I be doing this?

---

### Post by TheFu on 2020-11-23
ntfs or other non-linux file systems only support ownership control through mount options.

For ext2/3/4 and other native linux file systems just use **sudo chown** with the correct options.

Beextremely careful running a g program with sudo.  There can be unintended consequences. In general, it is best to avoid running gui programs under sudo. I can think of 1 or 2 exceptions - none are file managers.

**df -Th** will show the file system for all mounted storage.

---

### Post by Dennis N on 2020-11-23
If the file systems are ext4:
 
Use the terminal. If the mount point of the file system is /mnt/Data and your user name is tom, the command to change the owner to tom is:
```
sudo chown tom /mnt/Data
```
You can also change the group ownership of file system to xxxx at the same time if you use:
```
sudo chown tom:xxxx /mnt/Data
```

---

