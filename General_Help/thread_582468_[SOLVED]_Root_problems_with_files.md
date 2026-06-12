---
title: "[SOLVED] Root problems with files"
date: 2007-10-19
forum: General Help
---

### Post by RuB3N on 2007-10-19
I'm trying to add files to my /stuff partition. But you have to be root user to add it in there.
This is my computer and i should be root right? When I repartitioned my computer a couple days ago when i was getting ready for ubuntu 7.10 i created a user. But im not root.
how do i become root when i log in?

---

### Post by yabbadabbadont on 2007-10-19
Only the first user created is given admin privileges.  But if all users should be able to write to the /stuff filesystem, you could do the following:
```
sudo chgrp users /stuff
sudo chmod g+w /stuff

```
Then any local user should have write access to /stuff.

---

### Post by mlissner on 2007-10-19
It sounds like you want to be root when you log on just so you can work with that directory. If that's the case, it sounds like the owner of the directory is root. If so, what you want to do is a sudo chown -R $USER /stuff 

That will change the owner of all the files and directories in /stuff to the user that runs it. I wouldn't recommend it if it has a bunch of setting files or the like inside, but you might want to just do a sudo chown $USER /stuff if that is the case. That command won't change the ownership recursively.

---

### Post by RuB3N on 2007-10-19
This is the Error that come up when i dragged the file to the folder/ partition.

[COLOR="Red"]

Error while copying to "/stuff".

You do not have permissions to write to this folder.[/COLOR]

---

### Post by RuB3N on 2007-10-19
yea thanks that works!!

---

### Post by ilmuikhlas on 2007-10-19
logging in as non-root is not a problem. that's a default from ubuntu that the first user is USER (u gave the name). the way to run command that needs root privilege is using "sudo". why dont ubuntu allows u to logging as root? thats the way ubuntu avoids you from doing something horrible using root account

---

