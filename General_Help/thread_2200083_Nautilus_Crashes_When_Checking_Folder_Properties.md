---
title: "Nautilus Crashes When Checking Folder Properties"
date: 2014-01-17
forum: General Help
---

### Post by eldavar on 2014-01-17
Good morning friends. I've been experiencing a problem with Nautilus when used as root. 

If I right-click a folder and choose Properties, the Nautilus window instantly closes. In the terminal, the following error message appears: 
```
ERROR:nautilus-properties-window.c:1837:schedule_owner_change_timeout: assertion failed: (NAUTILUS_IS_FILE (file))
```
This does not happen when using Nautilus as a standard user. I wanted to try using the GUI the change some folder permissions, which is the reason for starting Nautilus with gksu. 

What does that error mean about changing the owner? Is this something that can be fixed by adjusting the timeout settings? If so, I don't know anything about how to do that either.

---

### Post by ibjsb4 on 2014-01-18
Don't know if this is any help, but found some bugs ..

[https://bugzilla.gnome.org/show_bug.cgi?id=700116](https://bugzilla.gnome.org/show_bug.cgi?id=700116)

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1106283](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1106283)

[https://bugzilla.gnome.org/show_bug.cgi?id=700492](https://bugzilla.gnome.org/show_bug.cgi?id=700492)

---

