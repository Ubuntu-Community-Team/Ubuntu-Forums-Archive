---
title: "Ubuntu-Tweak Error"
date: 2013-06-23
forum: General Help
---

### Post by SurfaceUnits on 2013-06-23
I get the following error when attempting to load Tweak

```
ubuntu-tweak
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
[utils.icon][WARNING] Icon 'gconf-editor' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'gconf-editor' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'gnome-session-hibernate' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'gnome-session-hibernate' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'application-octet-stream' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'application-octet-stream' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'gnome-app-install' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'gnome-app-install' not present in theme (icon.py:32)
[utils.icon][WARNING] get_from_list for folder-home failed, try next (icon.py:56)
[utils.icon][WARNING] get_from_list for folder-home failed, try next (icon.py:56)
[utils.icon][WARNING] Icon 'application-x-theme' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'application-x-theme' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'computerjanitor' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'computerjanitor' not present in theme (icon.py:32)

(ubuntu-tweak:24517): Gtk-ERROR **: GtkBox child GtkTreeView minimum width: -1 < 0 for height 352
Trace/breakpoint trap (core dumped)


```

---

### Post by lidex on 2013-06-24
What are your vitals?

```
lsb_release -a
```

```
dpkg-query -l libgtk-3-bin
```

---

### Post by sandyd on 2013-06-24
[https://bugs.launchpad.net/ubuntu-tweak/+bug/1144075](https://bugs.launchpad.net/ubuntu-tweak/+bug/1144075)
See bug report above ^^

---

### Post by SurfaceUnits on 2013-06-24
```


~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring



```

```

~$ dpkg-query -l libgtk-3-bin
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version               Architecture          Description
+++-=================================-=====================-=====================-=======================================================================
ii  libgtk-3-bin                      3.8.2-0ubuntu6~raring amd64                 programs for the GTK+ graphical user interface library



```

---

