---
title: "trying to update pidgin caused has stopped other programs from updating . Help please"
date: 2007-06-01
forum: General Help
---

### Post by maddbaron on 2007-06-01
I am still using edgy eft.


I found a deb on the site for the newest pidgin it said remove my old pidgin so I did tried installing the deb's libpurple01 and pidgin, Kwwp getting unmet errors and other errors can someone help me clean this up

was told to autoremove by the system and got this
> You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libpurple0: Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is installed
              Depends: libdbus-1-3 (>= 0.94) but 0.93-0ubuntu3.1 is installed
              Depends: libdbus-glib-1-2 (>= 0.73) but 0.71-1ubuntu1 is installed
              Depends: libglib2.0-0 (>= 2.12.9) but 2.12.4-0ubuntu1 is installed
              Depends: libxml2 (>= 2.6.27) but 2.6.26.dfsg-2ubuntu4 is installed
  pidgin: Depends: libatk1.0-0 (>= 1.13.1) but 1.12.3-0ubuntu1 is installed
          Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is installed
          Depends: libcairo2 (>= 1.4.2) but 1.2.4-1ubuntu2 is installed
          Depends: libdbus-1-3 (>= 0.94) but 0.93-0ubuntu3.1 is installed
          Depends: libdbus-glib-1-2 (>= 0.73) but 0.71-1ubuntu1 is installed
          Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-7ubuntu2 is installed
          Depends: libglib2.0-0 (>= 2.12.9) but 2.12.4-0ubuntu1 is installed
          Depends: libgstreamer0.10-0 (>= 0.10.12) but 0.10.10-1ubuntu2 is installed
          Depends: libpango1.0-0 (>= 1.16.2) but 1.14.5-0ubuntu1 is installed
          Depends: libpng12-0 (>= 1.2.13-4) but 1.2.8rel-5.1ubuntu0.1 is installed
          Depends: libsqlite3-0 (>= 3.3.13) but 3.3.5-0.2 is installed
          Depends: libxml2 (>= 2.6.27) but 2.6.26.dfsg-2ubuntu4 is installed
E: Unmet dependencies. Try using -f.

when i tried to install/upgrade my source code for my system the newest i got
> Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libpurple0 pidgin
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libpurple0 pidgin
0 upgraded, 0 newly installed, 2 to remove and 3 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
 
But I uninstalled these already...

I am very confused as to what to do, I can't upgrade my system and can't install the newest pdigin. I have the source file but I am very bad at compiling. 

Can someone please help?

---

