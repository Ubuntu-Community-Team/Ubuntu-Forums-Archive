---
title: "Disable application at Gnome startup"
date: 2008-01-24
forum: General Help
---

### Post by javierstowics on 2008-01-24
Hi all,

I succesfully installed beryl and after doing some updates to several packages, I couldn't log in the X session because after validating the username and password it keeps restarting the X server...:confused:

I found that the problem is with the beryl-manager...:( so I want to know how can I erase it from the application list that executes at the startup of the X session... 

Also, I would like to know if you had the same problem.

Thanks in advance!

---

### Post by ajgreeny on 2008-01-24
I don't run beryl, but use compiz-fusion instead - it's great!
To answer your problem, try to get a GUI by entering ```
killall beryl-manager
```and then try ```
startx
```which may give you the gnome desktop you want.
Now go to System>Preferences?Sessions, and remove beryl-manager from the startup list.

I'm sure you could do the whole thing in terminal, but I'm afraid I don't know how, so someone else will need to tell you, if my idea is not successful.

---

