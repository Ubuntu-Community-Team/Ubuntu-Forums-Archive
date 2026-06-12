---
title: "[ASK] Permission for Folder in Ubuntu"
date: 2013-08-02
forum: General Help
---

### Post by Indra_ivan on 2013-08-02
I have a question, can we make a folder cannot deleted but we can still modify it's content (adding a new file at least) ?

I already try several options like ```
chmod
``` or ```
chattr
```, but both of them lock folder modify, like we can't add new file, or some kind like that.

Please help me.

---

### Post by lukeiamyourfather on 2013-08-02
You can do it one of two ways. Either change the owner to your user or change the permissions to allow everyone to both read and write to the file. This is the command to change the owner of the folder (-R makes it recursively do subfolders too). Replace luke:luke with your username and group, by default the group is the same as the username.

```
sudo chown -R luke:luke foldername
```

This the command to change the permissions. So someone else could own the file but you could add permission to read and write (and delete it) to other people. The -R means the same as with chown, the a+rw means all users add read and write permission.

```
sudo chmod -R a+rw foldername
```

You can find out more about those commands with the man command (short for manual). There's even a manual for the manual.

```

man chmod
man chown
man man

```

---

### Post by coffeecat on 2013-08-02
Support question - not chat.

*Thread moved to **General Help**.*

---

