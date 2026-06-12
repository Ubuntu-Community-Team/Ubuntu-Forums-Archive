---
title: "add new user query"
date: 2008-01-05
forum: General Help
---

### Post by richardy on 2008-01-05
Hi,
I am running a Xubuntu system (feisty fawn) and have a query regarding adding new users and restricting there access to certain directories. Basically i did the following:
Making use of "users settings" i set up a new user with a user name and password, all went fine. i set up the new user initially in my group and then in the group users.  Currently all files on the computer are owned by me so assumed that any new user i set up would not have access to my home directory however what seems to have happened is that they now have access to everything (including my home directory)  but i do not have access to there home directory but what i want is a situation where i do not have access to there home directory and they also do not have access to my home directory (as it should be) but i cant seem to get this to happen. Any help would be much appreciated.

Cheers.

---

### Post by dhk on 2008-01-06
Try looking at the permission flags on the home directories:
```

$ ls -l /home
total 20
drwxr-xr-x 24 dhk  dhk   4096 2008-01-06 19:02 dhk

```The string "drwxr-xr-x" shows the permissions of the given file or directory. The d tells us that this is a directory and the next 9 characters are the actual permission flags. They are three blocks of three characters each. The first block ("rwx") means that the owner has read (r), write (w) and execute (x) permissions. The second block ("r-x") means that the group has read and execute permissions, but is not allowed to write. The third block ("r-x") means that others have the same permissions as the group.

Your description indicates that your home directory has the same permissions as mine, while the new user's home directory has "rwx------" (no permissions for group and others).

You can change permissions using the [chmod]("http://en.wikipedia.org/wiki/Chmod") command. In my case, the command would be:
```

$ chmod go-rx /home/dhk
$ ls -l /home
total 20
drwx------ 24 dhk  dhk   4096 2008-01-06 19:02 dhk

```"go" means that we want to change permissions for group and others, and "-rx" means that we want to remove read and execute permissions.

I hope this helps.

---

