---
title: "I killed my apt..."
date: 2007-08-18
forum: General Help
---

### Post by mpgarate on 2007-08-18
I mucked up something when trying to install ubuntustudio... any ideas?

> mike@mike-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  ardour-gtk
The following NEW packages will be installed:
  ardour-gtk
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
134 not fully installed or removed.
Need to get 0B/2493kB of archives.
After unpacking 6779kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 154164 files and directories currently installed.)
Unpacking ardour-gtk (from .../ardour-gtk_0.99.3-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/ardour-gtk_0.99.3-1_i386.deb (--unpack):
 trying to overwrite `/usr/share/locale/ru_RU/LC_MESSAGES/libardour.mo', which is also in package ardour
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ardour-gtk_0.99.3-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
mike@mike-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  ubuntustudio-audio: Depends: ardour-gtk
E: Unmet dependencies. Try using -f.
mike@mike-desktop:~$ 


---

### Post by taurus on 2007-08-18
Try something like

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by mpgarate on 2007-08-18
nope... still getting the same errors :(

---

