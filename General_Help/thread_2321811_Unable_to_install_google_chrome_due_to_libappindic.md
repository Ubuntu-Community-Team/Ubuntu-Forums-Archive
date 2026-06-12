---
title: "Unable to install google chrome due to libappindicator"
date: 2016-04-24
forum: General Help
---

### Post by ihtruelsen on 2016-04-24
I am trying to install google chrome on a fresh install of 16.04 (64bit). I have done an update and dist-upgrade before attempting.

When I try to install the .deb package, I get:
```

 sudo dpkg -i google-chrome-stable_current_amd64.deb 
Selecting previously unselected package google-chrome-stable.
(Reading database ... 173378 files and directories currently installed.)
Preparing to unpack google-chrome-stable_current_amd64.deb ...
Unpacking google-chrome-stable (50.0.2661.86-1) ...
dpkg: dependency problems prevent configuration of google-chrome-stable:
 google-chrome-stable depends on libappindicator1; however:
  Package libappindicator1 is not installed.

dpkg: error processing package google-chrome-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160415-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Errors were encountered while processing:
 google-chrome-stable

```

So, I try to install libappindicator:
```

sudo apt-get install libappindicator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libappindicator

```

Then thinking that it might be a -dev package, I try:
```

sudo apt-get install libappindicator-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 google-chrome-stable : Depends: libappindicator1 but it is not going to be installed
 libappindicator-dev : Depends: gir1.2-appindicator-0.1 (= 12.10.1+15.04.20141110-0ubuntu1) but it is not going to be installed
                       Depends: libdbusmenu-glib-dev (>= 0.1.8) but it is not going to be installed
                       Depends: libdbus-glib-1-dev (>= 0.76) but it is not going to be installed
                       Depends: libappindicator1 (= 12.10.1+15.04.20141110-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

The -f option gives the same output.

I don't want to get too far into the weeds installing package versions before checking to see if i am missing something simple, or at least, simpler.

Am I missing something?

---

### Post by ptn107 on 2016-04-24
```
apt-get install libappindicator1
```

---

### Post by deadflowr on 2016-04-25
> **ptn107 said:**
> ```
apt-get install libappindicator1
```

or
```
sudo apt-get install -f
```

either method should pull in the libappindicator packaeg.
The install -f command, though, will pull it in and also finish the chrome install while it's at it.

---

