---
title: "Desktop Shortcuts"
date: 2015-10-23
forum: General Help
---

### Post by poorguy on 2015-10-23
hello all,

i am wanting to know if there is an easy way to create desktop shortcuts for websites that i vist often. Ubuntu 14.04 is my distro used.

thanks.

---

### Post by ajgreeny on 2015-10-23
You can do that if you really want to by copying the **firefox.desktop** or other web-browser .desktop file from /usr/share/applications to the Desktop folder in your home.

Now open the firefox.desktop file in gedit (or any other text editor) find the line 
**Exec=firefox %u** and edit it to 
**Exec=firefox [noparse]www.ubuntuforums.org[/noparse]** 

I've shown this forum site as an example.

If you have exo-tools installed you can also do it with command 
**exo-open [noparse]www.ubuntuforums.org[/noparse]**
which will open that site in your preferred browser application.

---

### Post by poorguy on 2015-10-23
ok i will try that out and see how good i do.

thanks for the help.

---

