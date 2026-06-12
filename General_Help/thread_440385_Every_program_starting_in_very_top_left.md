---
title: "Every program starting in very top left"
date: 2007-05-11
forum: General Help
---

### Post by Sqweeks on 2007-05-11
For some reason all of a sudden every program i start will be in the very top left corner and i am unable to get to the title bar to move them. Any idea how to fix this?

---

### Post by deepwave on 2007-05-11
Are you using Gnome, KDE, or xfce?  Also, is that the programs have no title bar, or that X is displaying the entire top part of the desktop above the screen?

---

### Post by Sqweeks on 2007-05-11
I am using Gnome. It apears to have no title bar but if i open another instance of the program it will be in the middle and have a title bar. I am also having a 2nd problem when adding programs to the sessions startup area. Ill add /usr/bin/beryl-manager but every time i hit close it wont be in there anymore and will never start up when i start ubuntu.

---

### Post by aidanr on 2007-05-11
beryl has an option for placement of newly opened programs, i'm at work at the moment though and can't remeber where it is

try: 
```
sudo chown -R username ~/.config
sudo chgrp -R username ~/.config
sudo chmod -R 755 ~/.config
```
for the second problem

---

### Post by Sqweeks on 2007-05-11
thanks

---

### Post by GedB on 2007-05-13
I have the same problem.  I think it is already reported here:

[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/106350](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/106350)

---

