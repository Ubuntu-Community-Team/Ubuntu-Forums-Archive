---
title: "Installed maple. How to run it?"
date: 2008-05-30
forum: General Help
---

### Post by Svopp on 2008-05-30
Hey there,

I have installed maple 11 and installed it into /root/maple11/

Im running Ubuntu 8.04 and it doesnt show up anyplace in the application menu.
I also tried ALT+F2 and typed maple, but it doesnt give any suggestions to start the program.

Thirdly i searched through the installation folder, but couldnt find which file to execute.

Any help appreciated :)

---

### Post by sonofusion82 on 2008-05-30
i m not familiar with maple, but i feel that it is generally not wise to install user application to /root

---

### Post by ad_267 on 2008-05-30
/root is the home folder for the root user

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

If you don't install something with the package manager it usually goes in /usr/local or /opt

The installer also may not create any launchers in your menu. You can try running it by typing maple into a terminal. If that works then create a launcher for that command. You can edit your menu by right clicking on the menu icon and select edit menus. You may need to create a link to the binary in /usr/local/bin

Edit:
Read this, it explains everything you need to do: [https://help.ubuntu.com/community/Maple](https://help.ubuntu.com/community/Maple)
Just did a google search for "ubuntu install maple"

---

### Post by jamaas on 2008-05-30
You might try opening a terminal and typing
"xmaple"

Jim

---

### Post by Perfect Storm on 2008-05-30
How did you install it in the first place? Can you post, as it will be useful to help out your problem.

---

