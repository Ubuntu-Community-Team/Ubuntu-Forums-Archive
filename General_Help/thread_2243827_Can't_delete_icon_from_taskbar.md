---
title: "Can't delete icon from taskbar"
date: 2014-09-11
forum: General Help
---

### Post by alan93 on 2014-09-11
I have removed an app using the software center but now the icon will not go away.
I have tried reinstalling and removing but that does not work.
I have tried every combination of mouse clicks, even windows key +alt + right click but nothing will remove that icon or give an option to do so.

The icon will not launch the app when it is installed. I have to search the app using Dash Home search and then click the search result.

---

### Post by ian-weisser on 2014-09-13
Which application?

When installing or uninstalling, do you get any error messages?
If so, what exactly are they?

After uninstalling the application, look in /usr/share/applications.
Is the application's .desktop file still there? If so, delete it.
Warning: Do _not_ delete the desktop file while the application is installed.

---

