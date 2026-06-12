---
title: "Crashed Ubuntu"
date: 2007-03-17
forum: General Help
---

### Post by Moe70 on 2007-03-17
I've been playing around with the xserver all day today trying to install beryl. and i must have corrupted it and when i restarted i couldnt get back on. before the login screen comes up it says 'failed to start the x server.....Myabe its not set correctly'

and it loads the login without graphics just text... i can enter my username and password and log in ...and enter terminal commands.... 

do i need to format or is there a way to reinstall the x server from terminal/commands

---

### Post by peabody on 2007-03-17
From a terminal try:

sudo dpkg-reconfigure xserver-xorg

Walk through the wizard, set it up, and see if that fixes the problem.

---

