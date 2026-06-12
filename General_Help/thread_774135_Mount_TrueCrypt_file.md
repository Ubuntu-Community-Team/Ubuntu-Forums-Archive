---
title: "Mount TrueCrypt file"
date: 2008-04-29
forum: General Help
---

### Post by nami on 2008-04-29
Is it possible to change the mount options when mounting a truecrypt file via the gui so apache can have access to it.  I have tried a default mount and apache cannot access it at all.

---

### Post by skywalkin1138 on 2008-05-15
Not directly (it sets the user id and group id to you) and makes all files and directories under the mount directory only readable by you.

You could add the "apache" user to your "group" ("System->Administration->Users and Groups", press"Unlock" then "Manage Groups")
Once you have the volume mounted, you can use a Terminal and call "chmod" to set permissions for the group.

  chmod -R g+rx [path to mount directory]

This should grant read access as well as the ability to traverse the filesystem.

---

### Post by bodhi.zazen on 2008-05-15
If truecrypt will not do this, LUKS will.

[http://ubuntuforums.org/showthread.php?t=404346](http://ubuntuforums.org/showthread.php?t=404346)

Go ahead and make your crypt. Mount it. Once mounted

sudo chown root.apache /mount/point
sudo chmod 770/mount/point

---

