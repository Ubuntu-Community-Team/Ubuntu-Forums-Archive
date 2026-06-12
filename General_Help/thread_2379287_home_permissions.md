---
title: "home permissions"
date: 2017-12-03
forum: General Help
---

### Post by shoeleshunter78 on 2017-12-03
What are the default permissions of a user's home?

The user I created when installing the system has a home directory with permissions of 700, but subsequent user directories have 755 set.

---

### Post by SeijiSensei on 2017-12-03
Ubuntu uses 755 permissions for home directories as part of its "sharing" ethic. Distributions like RedHat which are more server-oriented use 700 permissions.

---

### Post by shoeleshunter78 on 2017-12-04
That seems rather insecure. So if I'm not mistaken, anyone on an Ubuntu system can read my private documents?

---

### Post by apmcd47 on 2017-12-04
You can change the default permissions of a new users' home directory by changing the value of UMASK in /etc/login.defs.

You can change the default umask for each user (the mask that decides the permissions for any new file or directory a user creates) by adding a umask command in the /etc/profile file. Similarly you can alter the umask in /etc/skel/.profile for future users. 

Personally, you can alter the umask for yourself in either ~/.profile or ~/.bashrc (assuming you are using bash).

You can change the permissions of files and directories after they have been created using chmod.

You just have to remember to do this next time you install a fresh Ubuntu. On the other hand you could create a shell script to do this for you and include it in a "shopping list" of tasks to run after every installation.

Andrew

---

### Post by SeijiSensei on 2017-12-04
You can still have 755 permissions on a home directory yet limit access to the files those directories contain.  The most effective method is to change your "umask" from 022 to 077.  That value is the octal complement of the permission mask.  So a value of 022 results in permissions of 755 on directories and 644 (readable by everyone) on files.

You'll find the entry for umask in /etc/login.defs.  Edit that file as root with sudo and change the line

```
UMASK           022
```

to 

```
UMASK           077
```

Then any file or directory you create will by default only be readable by you.  The same restrictions will apply to all other users.

You can override umask's for individual users by including a umask command in /home/username/.profile. A savvy user can change that back, though.

---

