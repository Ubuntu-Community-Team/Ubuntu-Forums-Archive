---
title: "Help me create a desktop launcher for a network folder"
date: 2007-05-31
forum: General Help
---

### Post by hurtstotalktoyou on 2007-05-31
So, I have no problem navigating to a Windows PC on my home network from Ubuntu Studio.  I even created a shortcut for a particular folder in the ¨Places¨ drop-down menu.  However, I´d like to create a shortcut on my desktop, as well.  I´ve tried using the right-click and ¨create launcher¨ option, but it will only allow me to choose a file, not a folder.  I´ve also tried application, using the following command line:  open ´smb://computer/driveletter/folder´  (the command which appears when I hover over the shortcut in the Places menu)  That doesn´t give me an error message, but neither does it open any folder.

Any suggestions?

Thanks in advance!

---

### Post by awkwardmoment on 2007-05-31
You might try creating a launcher with the following settings:
Type: application
Command: nautilus /path/to/your/folder

---

