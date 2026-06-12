---
title: "Configuring Catfish 1.0.2"
date: 2016-02-06
forum: General Help
---

### Post by marcerickson on 2016-02-06
How can I change the default directory that Catfish starts its search  in? I don’t want to have to click the drop down to change from /home –  99% of my searches are on a different drive. I’m using Lubuntu 14.04  with the LXDE desktop.

---

### Post by Dennis N on 2016-02-06
Use the menu editor and change the command to launch catfish by adding --path= followed by full path to directory.

To default to Documents:

catfish --path=/home/user-name/Documents

Of course, substitute your user name here.

---

### Post by oldos2er on 2016-02-06
Moved to General Help.

---

