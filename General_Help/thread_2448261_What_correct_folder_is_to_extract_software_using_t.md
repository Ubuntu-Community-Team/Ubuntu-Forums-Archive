---
title: "What correct folder is to extract software using tar extension ?"
date: 2020-08-05
forum: General Help
---

### Post by aug7744 on 2020-08-05
Using Lubuntu 20.04.
I have downloaded an browser and extracted in desktop and is working perfectly.
Well an folder in desktop for an software not look correct.
What is the correct folder to extract softwares that is in tar files ?

---

### Post by RikoW on 2020-08-05
Hi there,

i'd put the extracted directory into /opt/ and create a link to the (browser) executable in /usr/bin or maybe /usr/local/bin.
Maybe you have to copy a .desktop file into $HOME/.local/share/applications to have it appear in your menu.

Cheers!

---

### Post by Impavidus on 2020-08-05
The proper directory for stuff installed without using the package manager is /usr/local/. The executable belongs in /usr/local/bin/, config files in /usr/local/etc/, supporting data files in /usr/local/share, etc. Instead, you can also install it in /opt/appname/. If you install something for a single user, you can leave the files in your home directory, like ~/bin/, ~/.local/share/, etc. It depends a bit on how well-behaved the application is. Some just don't follow the guidelines and won't find their data files if installed in the standard UNIX way (like applications designed for Windows and later ported to Linux).

---

### Post by pbear42 on 2020-08-05
It depends.  See [https://askubuntu.com/questions/1148/when-installing-user-applications-where-do-best-practices-suggest-they-be-loc](https://askubuntu.com/questions/1148/when-installing-user-applications-where-do-best-practices-suggest-they-be-loc)

---

### Post by TheFu on 2020-08-05
Don't pollute the formal package directories. 

Stay with /usr/local/ for all non-commercial software.  I'd keep the directory structure the tar file creates, just under /usr/local/  Follow what the file system hierarchy standards say. [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

/opt/ is usually for commercial or closed-source programs that don't have a package for ubuntu.

But really, going out and downloading programs on the internet outside the package manager is to be avoided.  It is the last choice in the list of 5 other methods.

---

### Post by HermanAB on 2020-08-06
Note: Always tar a directory.  Never tar a bunch of files.

As mentioned by others, /usr/local is for user installed programs.  It will not get overwritten when you do system updates.

---

### Post by aug7744 on 2020-08-13
Thanks very much :)

---

