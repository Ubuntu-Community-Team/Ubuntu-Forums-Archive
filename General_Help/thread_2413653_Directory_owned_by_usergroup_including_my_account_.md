---
title: "Directory owned by usergroup including my account only accepts modifications by root"
date: 2019-02-28
forum: General Help
---

### Post by lucy5 on 2019-02-28
My /var/www directory is owned by www-data:www-data. My user account is in the www-data group. However, whenever I access a file there (using Sublime 3) and try to save, I'm asked for a password. I have to use sudo in the terminal to do anything in the directory or get 'permission denied'. What am I doing wrong?

---

### Post by Impavidus on 2019-02-28
Has the group write permission on the directory? That's necessary to create or delete files. Is the file assigned to the same group and has the group write permission on the file? That's necessary to edit the file.

---

### Post by lucy5 on 2019-02-28
> drwxr-xr-x
This means it doesn't, right? Strange, I assumed the 'owner' would have all permissions... How should I set this up so it works properly?

Edit: Nevermind, I found it here: [https://askubuntu.com/questions/162866/correct-permissions-for-var-www-and-wordpress](https://askubuntu.com/questions/162866/correct-permissions-for-var-www-and-wordpress)
Thanks for the help :)

---

### Post by deadflowr on 2019-02-28
owner and groups are different things, and do not bleed rights from one into the other.
Just because owner can do something does not mean group can do the same.

Use chmod to change permissions. You have several options, but I usually go the simplest (or I think it is)
```
sudo chmod 775 -R /path/to/folder/
```
See: [https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

---

