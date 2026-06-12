---
title: "Why can't I write on external HDs?"
date: 2007-05-01
forum: General Help
---

### Post by Bou on 2007-05-01
When I mount an external (USB) HD I can't write on it, and when I check its permissions I get the attached information.

Is that how it's meant to be? What can I do to be able to write on my HD?

---

### Post by Bou on 2007-05-01
I forgot the actual screenshot:

---

### Post by KIAaze on 2007-05-01
I think it's because you mounted it as root and didn't give yourself as user write permissions.

<edit: solution given wouldn't work (forgot x bit and chown,chgrp)>

---

### Post by KIAaze on 2007-05-01
Wait, I made a mistake. Here's how you should procede:
```
sudo chown <your_login> <directory where HD is mounted>
sudo chgrp <your_login> <directory where HD is mounted>
sudo chmod 755 <directory where HD is mounted>

```

If this doesn't work, then it's probably because the disk was mounted as read-only.
Unmount the disk by doing ```
umount <directory where HD is mounted>
```
Remount it as read/write by doing ```
mount -w <device (ex: /dev/hda1)> <directory where HD is to be mounted>
```
========================================================
_A little lesson about permissions:_

1)The permissions:
There are 3 types of permissions:
-read=r
-write=w
-execute=x (also necessary for entering folders)
And 3 "permission groups":
-owner/user
-group
-other

Permissions can be written in 2 ways:
a)rwx rwx rwx
b) x      y     z    where x, y and z are numbers corresponding to the binary form of rwx

ex:
user group other
rwx  r-x   r-x
421 421 421
 7      5     5

2)To see the permissions of a file: ```
ls -l <file>
```

3)To see the permissions of a folder: ```
ls -ld <folder>
```

4)To change the owner of a file/folder, use ```
chown <new_owner> <file/folder>
```

5)To change the group of a file/folder, use ```
chgrp <new_group> <file/folder>
```

6)To change the permissions of a file/folder, use ```
chmod <xyz> <file/folder>
```
There are also other ways to change permissions, like using +x, +w, etc
Type ```
man chmod
``` for more info.

---

