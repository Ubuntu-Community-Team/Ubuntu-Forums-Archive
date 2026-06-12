---
title: "Dependency problems with gtk/python - applications not working"
date: 2006-12-18
forum: General Help
---

### Post by jonah1980 on 2006-12-18
hi guys, i've somehow messed up something and now loads of apps won't work for me. i can't load add/remove, bittorrent, appollon... etc

i tried updating and reinstalling certain packages but i get errors:

> naylor@naylor-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up python-gtk2 (2.10.3-0ubuntu3) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 281, in ?
    process(basedir,install_modules(py_installed))
  File "/usr/sbin/update-python-modules", line 154, in process
    func(basedir, dir, file)
  File "/usr/sbin/update-python-modules", line 126, in install_modules_func
    os.symlink(fullpath,destpath)
OSError: [Errno 20] Not a directory
dpkg: error processing python-gtk2 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-glade2:
 python-glade2 depends on python-gtk2 (= 2.10.3-0ubuntu3); however:
  Package python-gtk2 is not configured yet.
dpkg: error processing python-glade2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2:
 python-gnome2 depends on python-gtk2 (>= 2.8.6-1); however:
  Package python-gtk2 is not configured yet.
dpkg: error processing python-gnome2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-desktop:
 python-gnome2-desktop depends on python-gtk2 (>= 2.9.2); however:
  Package python-gtk2 is not configured yet.
dpkg: error processing python-gnome2-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-extras:
 python-gnome2-extras depends on python-gtk2 (>= 2.9.2); however:
  Package python-gtk2 is not configured yet.
 python-gnome2-extras depends on python-gnome2-desktop; however:
  Package python-gnome2-desktop is not configured yet.
dpkg: error processing python-gnome2-extras (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-vte:
 python-vte depends on python-gtk2; however:
  Package python-gtk2 is not configured yet.
dpkg: error processing python-vte (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-gtk2
 python-glade2
 python-gnome2
 python-gnome2-desktop
 python-gnome2-extras
 python-vte
E: Sub-process /usr/bin/dpkg returned an error code (1)


can anyone please help. thanks...

---

### Post by jonah1980 on 2006-12-19
ok i tried loading my add/remove command from terminal and the error msg mentioned gconf. so i've reinstalled all sorts to do with that but now i get this error:

> naylor@naylor-desktop:~$ /usr/bin/gnome-app-install
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 137, in ?
    from AppInstall.AppInstall import AppInstall
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 53, in ?
    import dbus
  File "/usr/lib/python2.4/site-packages/PIL/__init__.py", line 1, in ?
    #
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 45, in ?
ImportError: No module named dbus_bindings


any help would be greatly appreciated. thanks...

---

### Post by jonah1980 on 2006-12-19
a dude in the irc channel helped fix all this so it's working now...

---

### Post by raul_ on 2006-12-19
Post the solution here anyway :)

---

