---
title: "Firefox will not run"
date: 2008-06-22
forum: General Help
---

### Post by Los Frijoles on 2008-06-22
I recently upgraded from Ubuntu 6.06 to Ubuntu 8.04. After upgrading, Firefox refused to run. When I clicked the firefox icon in the menu bar, it would make a "Starting Firefox Web..." box which would eventually disappear and not start firefox. When I run firefox with the command 'firefox' from the command line, I get the message "Could not find compatible GRE between version 1.9 and 1.9."

Has anyone else had this problem? How do I fix it?

---

### Post by WeeWoh on 2008-06-22
Try running ```
sudo apt-get install firefox
``` from terminal. If it says that firefox is already installed then type ```
apt-get -f install firefox
``` in terminal. It should reinstall Firefox.

---

