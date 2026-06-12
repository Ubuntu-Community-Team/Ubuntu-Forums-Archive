---
title: "Problem Editing Startup Programs [Resolved]"
date: 2006-12-03
forum: General Help
---

### Post by golf22r on 2006-12-03
Whenever I try to edit the startup programs under sessions, it allows me to add commands, but it does not save them.  The next time I login the changes are gone.  Does anybody know why this is happening?  I am running Ubuntu 6.10.  Thank you.

---

### Post by aysiu on 2006-12-03
Maybe you should check that you own everything in your home directory? ```
sudo chown -R *username:username* /home/*username*
``` where *username* is your actual username.

---

### Post by norman_ on 2006-12-03
There is indeed a problem with config file ownership in the virgin edgy install. 

changing ownership of ~/.gnome2/session should fix it. Maybe this should be reported as a minor bug/annoyance

See this thread (there are a few others as well)
[http://www.ubuntuforums.org/showthread.php?t=122659&highlight=gnome+startup+programs](http://www.ubuntuforums.org/showthread.php?t=122659&highlight=gnome+startup+programs)

---

### Post by golf22r on 2006-12-03
How do I change the ownership of ~/.gnome2/session.  I found the file, but could not find how to change ownership.

---

### Post by taurus on 2006-12-03
> **golf22r said:**
> How do I change the ownership of ~/.gnome2/session.  I found the file, but could not find how to change ownership.
As aysiu described.

```
sudo chown **username**:**username** ~/.gnome2/session
(where **username** is your actual username...)
```

---

### Post by golf22r on 2006-12-03
Problem Solved!  Thank you for your help!

---

