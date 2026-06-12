---
title: "File permission problem"
date: 2014-05-28
forum: General Help
---

### Post by new_tolinux on 2014-05-28
Hi,

I tried a bunch of google results, but I couldn't find an answer for this.
I have a folder and it's chmodded g+s, so it inherits the group on file creation.
But for some reason, the system decides to grant only read permissions for the group on new files, even though the folder has rwx for the group.

Any idea what I'm missing?

Update:
In the meantime I tried installing the ACL (as suggested here: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) ) but that also didn't work on newly created files.

---

### Post by btindie on 2014-05-28
Setting chmod g+s only affects the group ownership, nothing to do with the permissions of the newly created file. See 'man chmod'

What's your 'umask' set to? I think it should be 'umask 0002' for what you want, [http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html](http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html)

---

### Post by new_tolinux on 2014-05-28
I don't really know what did the trick, but I started to set the umask to 007.
Next thing, I configured samba with "force create mode = 660"
At least the group has write permission now, I'm still not sure though why newly created files get rw-rw-r--, since both the 007 (even tried 0007) and the samba configuration are set to grant no rights to "others"

---

