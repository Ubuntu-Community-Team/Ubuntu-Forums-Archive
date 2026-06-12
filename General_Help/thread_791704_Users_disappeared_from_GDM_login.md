---
title: "Users disappeared from GDM login"
date: 2008-05-12
forum: General Help
---

### Post by Doughy on 2008-05-12
The users that were displayed for selection in the GDM login window have suddenly disappeared.  Now, I have to type the username as opposed to choosing it from the list with the mouse.

I did an ubuntu update yesterday and I wonder if something got messed up during the upgrade.  Anyone know what to do?  I'm running ubuntu 8.04.

Thanks.

---

### Post by y-lee on 2008-05-12
At System -> Admin -> Login Window, there is a drop-down menu in the Local tab called "Themed with face browser". Does selecting this help your issues?

---

### Post by chrisccoulson on 2008-05-12
See bug [/bin/bash not in /etc/shells, causing login window/fast user switch applet hilarity]("https://bugs.launchpad.net/ubuntu/hardy/+source/bash/+bug/228931")

---

### Post by Doughy on 2008-05-12
The workaround in that bug fixed the problem.  It looks like there was an issue with a recent update.  Thanks for posting the bug.

---

