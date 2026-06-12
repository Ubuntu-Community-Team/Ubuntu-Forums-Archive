---
title: "I need help installing a SH file"
date: 2021-11-25
forum: General Help
---

### Post by braznyc on 2021-11-25
The name of the program is Emboidermodder.


Any help is welcome.
I forgot how to install a .sh file.


Thanks.

---

### Post by yancek on 2021-11-25
An sh file is simply a script which you make executable and run in a terminal.  More info on where yo got it and what it does might help someone to help you.

---

### Post by braznyc on 2021-12-07
Thanks, Yancek.
I'm trying to install a software called "Embroidermodder".

---

### Post by Impavidus on 2021-12-07
An .sh file is usually a shell script. Usually, as there are no hard rules for filename extensions. You just put it in a directory that's in your PATH and make sure it has execute permissions for all who want to use it. Use```
echo $PATH
``` to see a colon-separated list of directories where you can put it, but avoid the directories used for stuff installed by the package manager. In other words, put it in ~/bin, ~/.local/bin (both for one user) or /usr/local/bin (for all users), unless you can think of a good reason to put it somewhere else. If installing for all users, you give read and execute permission to all, but make the file owned by root and only give root write permissions: 0755. Once you've done so, you can execute the file in the terminal.

---

