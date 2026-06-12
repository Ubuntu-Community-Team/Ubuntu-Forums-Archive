---
title: "Google Chrome not working In LUbuntu"
date: 2018-05-23
forum: General Help
---

### Post by gauravashara on 2018-05-23
I recently just download crhome latest version and installed it in my Lubuntu 16.04. 


When I tries to start from terminal getting following error. 

gaurav@gaurav-pc:~/Downloads$ **sudo dpkg -i --force-depends google-chrome-stable_current_amd64.deb**
Selecting previously unselected package google-chrome-stable.
(Reading database ... 216909 files and directories currently installed.)
Preparing to unpack google-chrome-stable_current_amd64.deb ...
Unpacking **google-chrome-stable (66.0.3359.181-1) **...
Setting up google-chrome-stable (66.0.3359.181-1) ...
update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/x-www-browser (x-www-browser) in auto mode
update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode
update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/google-chrome (google-chrome) in auto mode
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
gaurav@gaurav-pc:~/Downloads$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gaurav@gaurav-pc:~/Downloads$ google-chrome
**Bus error (core dumped)**

---

### Post by Perfect Storm on 2018-05-23
Thread moved to General Help.

---

### Post by gauravashara on 2018-05-25
Getting same error check all dependency

---

