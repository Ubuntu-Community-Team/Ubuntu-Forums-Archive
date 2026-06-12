---
title: "Install a standalone program"
date: 2007-09-27
forum: General Help
---

### Post by Prometheus7 on 2007-09-27
I downloaded eclipse europa from the eclipse web site and noticed that it is a standalone version. How can I install this so that I can type "eclipse" into the terminal and have it run? 

In general how do you install such a program? Do you just drop the exec in the bin dir?

Thanks a lot!

---

### Post by prince_niceguy on 2007-09-27
just install the eclipse and modify your .bashrc and include the eclipse root directory to your path.

so whenever your type eclipse it will start eclipse from the eclipse install directory.

---

### Post by Prometheus7 on 2007-09-27
Thanks -- is that what the repo does? I was under the impression that it puts all of the files in a certain place?

---

### Post by Prometheus7 on 2007-09-28
I also would like the program to show up in the applications menu -- how do I do all of this?

---

### Post by prince_niceguy on 2007-09-28
well technically yes, thats what repo do... they put the files in /usr/bin which is part of the path for all the users by default.

To add a new menu item just right click on the menu and select new launcher. i am sorry i am using kde and currently do not have gnome to try this out. 

it will ask for details like name, command and icon. fill in the appropriate details and it should work for you.

---

### Post by Prometheus7 on 2007-09-28
thanks!

---

