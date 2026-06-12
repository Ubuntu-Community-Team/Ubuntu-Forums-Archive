---
title: "Firefox problem"
date: 2013-10-10
forum: General Help
---

### Post by sequimbob on 2013-10-10
I am having a problem with firefox.  When I try to open firefox I get the following error message: "Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features."

I uninstalled it by sudo apt-get remove --purge firefox
Then I tried re installing with sudo apt-get install firefox

This is the result of the installation. No problems that I can see. 

bob@bob-HP-Pavilion-g7-Notebook-PC:~$ sudo apt-get remove --purge firefox
[sudo] password for bob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  thunderbird-globalmenu
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  firefox* firefox-globalmenu* firefox-gnome-support*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 63.2 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 174157 files and directories currently installed.)
Removing firefox-gnome-support ...
Removing firefox-globalmenu ...
Removing firefox ...
update-alternatives: using /usr/bin/chromium-browser to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode.
update-alternatives: using /usr/bin/chromium-browser to provide /usr/bin/x-www-browser (x-www-browser) in auto mode.
Purging configuration files for firefox ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...

I then re installed with the following:

bob@bob-HP-Pavilion-g7-Notebook-PC:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree 
Reading state information... Done
The following package was automatically installed and is no longer required:
thunderbird-globalmenu
Use 'apt-get autoremove' to remove them.
Suggested packages:
ttf-lyx
The following NEW packages will be installed:
firefox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/28.3 MB of archives.
After this operation, 62.9 MB of additional disk space will be used.
Selecting previously unselected package firefox.
(Reading database ... 174050 files and directories currently installed.)
Unpacking firefox (from .../firefox_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Setting up firefox (24.0+build1-0ubuntu0.12.04.1) ...
Please restart all running instances of firefox, or you will experience problems

Then as instructed I did the following :

bob@bob-HP-Pavilion-g7-Notebook-PC:~$ sudo apt-get autoremove ttf-lyx
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Package ttf-lyx is not installed, so not removed
The following packages will be REMOVED:
thunderbird-globalmenu
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 133 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 174151 files and directories currently installed.)
Removing thunderbird-globalmenu ...

Firefox was not running so I attempted to start it and got the same error message listed above. I haven't found the profiles for firefox so I don't know if there is a permissions problem.
Anyone else have this problem?

---

### Post by fantab on 2013-10-10
Remove/Delete .mozilla (dotmozilla) in your Home Directory. Dot files are hidden, you can reveal them with Ctrl+H. Then restart Firefox.

---

### Post by sequimbob on 2013-10-12
Thanks.  That did the trick.  As a newbie, I appreciate your help.

---

