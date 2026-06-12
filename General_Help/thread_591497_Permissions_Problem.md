---
title: "Permissions Problem"
date: 2007-10-25
forum: General Help
---

### Post by Zipster90 on 2007-10-25
This isn't as much of a problem as much as it's a nuisance.

I was fiddling with the permissions for my home folder earlier today, hoping to make VirtualBox detect them, and the next time I rebooted my machine, Ubuntu pops up this error message after I enter my username and password:

> User's $HOME/.drmc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by users and not writable by other users.

After I click OK, it goes on it's merry way and everything boots and works fine. It's just really annoying. Did my fiddling cause this problem? How can I un-fiddle it? Thanks.:)

---

### Post by aks44 on 2007-10-25
This should do it:

```
$ sudo chown username:username ~/.drmc
$ chmod 644 ~/.drmc
```


Where "username" is your own user name, ie. /home/**username**/...



EDIT: FWIW, chown changes the file's owner. I made it sudo to make sure you could change it no matter your configuration. chmod changes the file's permissions.

---

### Post by Zipster90 on 2007-10-25
Okay. I tried that, but it returned this after I entered the first line:

```
chown: cannot access `/home/zach/.drmc': No such file or directory

```

I don't think I remember removing anything, so I don't know why it's not there.

---

### Post by Zipster90 on 2007-10-26
Bump.

Just wondering if anyone else had any ideas.

---

### Post by aks44 on 2007-10-26
Make sure to **chmod 755 /home/zach**

If it still doesn't work, maybe create an empty ~/.drmc and make sure it is chmod'ed 644 ?

---

