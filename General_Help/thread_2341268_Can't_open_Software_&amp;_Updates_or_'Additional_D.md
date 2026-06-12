---
title: "Can't open Software &amp; Updates or 'Additional Drivers' application"
date: 2016-10-26
forum: General Help
---

### Post by aguxez on 2016-10-26
[COLOR=#111111][FONT=Ubuntu]Today I started my computer and I wanted to check the software updater and it was not even opening; just crashing; same thing with Software & Updates (I want to install proprietary software) and I don't know, weird thing is that Software Updater started working but Software & Updates isn't opening. It just "try" to open but then closes immediately so I don't what to look for or what to try.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I checked for updates and upgrades on the terminal but didn't do anything.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Also tried sudo rm /var/lib/apt/lists/*
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thanks for any help.[/FONT][/COLOR]

---

### Post by howefield on 2016-10-26
> **aguxez said:**
> ...but Software & Updates isn't opening. It just "try" to open but then closes immediately so I don't what to look for or what to try.

What is the output from trying to open the Software & Updates application via terminal..

```
software-properties-gtk
```

---

### Post by aguxez on 2016-10-26
```
 Traceback (most recent call last):  File "/usr/bin/software-properties-gtk", line 37, in <module>
    from softwareproperties.gtk.SoftwarePropertiesGtk import SoftwarePropertiesGtk
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 34, in <module>
    from aptdaemon import client
  File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 43, in <module>
    import defer
ImportError: No module named 'defer' 
```

---

### Post by howefield on 2016-10-26
Also, missed that you tried updating via the terminal.. can you provide the actual output of the following - "didn't do anything" doesn't help anyone understand your issue very well.

```
cat /etc/*-release
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by aguxez on 2016-10-26
> **howefield said:**
> Also, missed that you tried updating via the terminal.. can you provide the actual output of the following - "didn't do anything" doesn't help anyone understand your issue very well.

```
cat /etc/*-release
```

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"
NAME="Ubuntu"
VERSION="16.04.1 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.1 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
UBUNTU_CODENAME=xenial
```

And sorry, with "didn't do anything" I mean that I checked for upgrades and updates on the terminal but everything was up to date.

---

### Post by howefield on 2016-10-26
Try [this thread]("http://askubuntu.com/questions/838301/importerror-no-module-named-defer-from-aptdaemon/838312") with the same issue which appears solved.

---

### Post by aguxez on 2016-10-26
I installed it but now I'm getting this when I try to open it:

```
/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:40: PyGIWarning: Gdk was imported without specifying a version first. Use gi.require_version('Gdk', '3.0') before import to ensure that the right version gets loaded.  from gi.repository import GObject, Gdk, Gtk, Gio, GLib
/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:40: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import GObject, Gdk, Gtk, Gio, GLib
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 37, in <module>
    from softwareproperties.gtk.SoftwarePropertiesGtk import SoftwarePropertiesGtk
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 54, in <module>
    from UbuntuDrivers import detect
ImportError: No module named 'UbuntuDrivers'

```

I'm starting to think that I mixed something in those folders and I didn't realize in time but I may be wrong.

---

### Post by aguxez on 2016-10-26
?

---

