---
title: "starting IntelliJ as root"
date: 2015-05-22
forum: General Help
---

### Post by soxterix on 2015-05-22
I have installed IntelliJ IDE and I have shortcut to the location: Exec="/opt/intellij/bin/idea.sh" When I click on this icon my application starts but when I try to use this location to open IntellJ as root: sudo /opt/intellij/bin/idea.sh then installation wizard shows up instead of already installed program. How can I open my application as root?

---

### Post by TheFu on 2015-05-24
You shouldn't run any GUI tool as root. There are many reasons for this. Far too many to list here.  Usually people do this as a crutch rather than learning about file and directory permissions on a multi-user OS. That is too bad, since it really is simple and elegant stuff.

There may be a great reason you need to do this, so .... if you just need to edit protected files and would like to use any editor, you can (and should) use **sudoedit**.
Add **export EDITOR=/opt/intellij/bin/idea.sh** to your ~/.profile or ~/.bashrc, then have at it - **sudoedit /path/to/file**

Hope that helps.  You can check out the manpage for the sudoedit command, if you'd like to know more.

---

