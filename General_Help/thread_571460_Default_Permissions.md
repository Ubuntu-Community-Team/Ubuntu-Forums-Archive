---
title: "Default Permissions"
date: 2007-10-09
forum: General Help
---

### Post by joestanton100 on 2007-10-09
Hi,

I run a web server with a few sites hosted, just switched over from windows.

Theres just one problem, i have PHP scripts, and any time i create a file it does not have enough permissions.

How can i make default 777 permissions for my web directory recursively, as i have already got a very large amout of files and folders i would like to also set the default permissions to.

I have heard about umask, but it seems not to work recursively, is this correct, and does anyone have a better way. I just want it for my webroot.

Thanks,

Joe

---

### Post by eph1973 on 2007-10-09
are you looking for a command like
```
chmod -R 777 ./*
```?

Note:  That would of course be starting from the directory you wanted to change the permissions from.

---

