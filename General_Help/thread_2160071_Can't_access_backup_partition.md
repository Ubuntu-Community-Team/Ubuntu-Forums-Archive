---
title: "Can't access backup partition"
date: 2013-07-05
forum: General Help
---

### Post by tuxpenguin42 on 2013-07-05
I reinstalled my system yesterday after creating a new partition and copying all my files to it as backup. I then over-wrote the existing system with the new installation. When I now try to copy the files I can't, as I don't have the permissions to. A bit of googling tells me that this is because the UUIDs are different. I already tried copying the files as root, but this then leads to me being unable to access these files in my own home directory. Also, when I try to change the permissions by opening nautilus as root, right-clicking on the partition, and changing the permissions so I have read/write to everything on it, it crashes with this error:

```
**
ERROR:nautilus-properties-window.c:1836:schedule_owner_change_timeout: assertion failed: (NAUTILUS_IS_FILE (file))


```

I know it's probably a simple problem with the permissions, but I don't really know what I'm doing with this sort of thing. Any help would be greatly appreciated.

EDIT: also, if this is in the wrong section, I apologise.

---

### Post by ajgreeny on 2013-07-05
It is probably best to just copy those old files to your new home, as root if necessary, then run the command ```
sudo chown -R username:username /home/username
``` to ensure you are the owner of everything in your home, followed by ```
chmod -R 755 /home/username
``` to give the correct permissions for everything.  Use your own username where I put "username" of course.

You can do this from a command line login, or from recovery mode if you have a problem logging in to your normal user GUI.  If using recovery mode you will not need sudo as that runs with root permissions.

---

### Post by tuxpenguin42 on 2013-07-05
That appears to have worked, thanks so much!

---

