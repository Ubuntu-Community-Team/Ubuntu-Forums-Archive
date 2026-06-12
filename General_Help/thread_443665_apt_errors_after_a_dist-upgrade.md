---
title: "apt errors after a dist-upgrade"
date: 2007-05-14
forum: General Help
---

### Post by nricciar on 2007-05-14
I recently did a fresh install of fiesty and was in the process of updating all the packages and my computer ended up crashing half way through.  After rebooting and finishing the apt upgrade 42 packages are refusing to configure.

```

root@dnmnet:/home/nricciar# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
42 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up gnome-user-guide (2.18.1-0ubuntu1) ...
dpkg: error processing gnome-user-guide (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of ubuntu-docs:
 ubuntu-docs depends on gnome-user-guide; however:
  Package gnome-user-guide is not configured yet.
dpkg: error processing ubuntu-docs (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-panel-data (2.18.1-0ubuntu3.1) ...
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 139
Setting up capplets-data (2.18.1-0ubuntu2.1) ...
dpkg: error processing capplets-data (--configure):
 subprocess post-installation script returned error exit status 139



... cut down to save room ...



Errors were encountered while processing:
 gnome-user-guide
 ubuntu-docs
 gnome-panel-data
 capplets-data
 gnome-control-center
 gnome-panel
 alacarte
 deskbar-applet
 ekiga
 eog
 evince
 evolution-common
 evolution
 evolution-exchange
 evolution-plugins
 file-roller
 gcalctool
 gnome-power-manager
 gnome-session
 gdm
 gedit-common
 gedit
 synaptic
 software-properties-gtk
 gnome-app-install
 gnome-games-data
 gnome-games
 gnome-netstatus-applet
 gnome-system-monitor
 gnome-utils
 gthumb
 language-selector
 nautilus
 nautilus-cd-burner
 restricted-manager
 rhythmbox
 tomboy
 gnome-system-tools
 update-manager
 update-notifier
 zenity
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have been unable to recover from this so far, and was hoping someone may have a solution to the problem im experiencing.

---

### Post by taurus on 2007-05-14
What happens when you run these two commands?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by nricciar on 2007-05-14
update works fine, aptitude upgrade gives me the same errors as above.

---

### Post by taurus on 2007-05-14
Try

```
sudo dpkg --configure -a
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by nricciar on 2007-05-14
no luck... dpkg --configure -a gives the same errors, clean and update work fine, and upgrade fails the same way.... guess its just time to reinstall it again, at least its a fresh install anyways.

---

