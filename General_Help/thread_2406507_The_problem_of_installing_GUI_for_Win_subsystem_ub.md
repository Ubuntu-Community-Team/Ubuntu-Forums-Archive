---
title: "The problem of installing GUI for Win subsystem ubuntu18.04"
date: 2018-11-21
forum: General Help
---

### Post by aex215 on 2018-11-21
Hi, 
I installed the windows subsystem ubuntu18.04, and I want to install the GUI. I am using Vcxsrv. After I type in ccsm in the bash, it has some error messages like:

```
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 94, in <module>
    import ccm
  File "/usr/lib/python2.7/dist-packages/ccm/__init__.py", line 1, in <module>
    from ccm.Conflicts import *
  File "/usr/lib/python2.7/dist-packages/ccm/Conflicts.py", line 26, in <module>
    from ccm.Constants import *
  File "/usr/lib/python2.7/dist-packages/ccm/Constants.py", line 30, in <module>
    CurrentScreenNum = gtk.gdk.display_get_default().get_default_screen().get_number()
AttributeError: 'NoneType' object has no attribute 'get_default_screen'
```

Please help me out!

---

### Post by Frogs Hair on 2018-11-21
> [COLOR=#000000]windows subsystem ubuntu18.04[/COLOR] Can explain what this is ? Could it be [this]("https://www.microsoft.com/en-us/p/ubuntu-1804-lts/9n9tngvndl3q?activetab=pivot:overviewtab")?

---

### Post by lisati on 2018-11-22
*Thread moved to **General Help**.*

Please clarify what you mean by "windows subsystem."

---

### Post by aex215 on 2018-11-22
Sorry,
Win10 has a Linux subsystem

---

### Post by #&amp;thj^% on 2018-11-22
Run these commands and check the output for each:
```

$ export DISPLAY=localhost:0
$ sudo service dbus start
* Starting system message bus dbus                 [OK]
$ echo $DISPLAY
localhost:0
```
example say you want and have gedit installed run:
Start gedit:
```

export DISPLAY=:0
gedit

```
P.S
You can add VcXsrv as a Win10 bootable: [https://winaero.com/blog/how-to-add-or-remove-startup-apps-in-windows-10/](https://winaero.com/blog/how-to-add-or-remove-startup-apps-in-windows-10/)

Also if needed more info found here: [https://superuser.com/questions/1075659/open-ubuntu-bashs-gui-applications-on-windows-10](https://superuser.com/questions/1075659/open-ubuntu-bashs-gui-applications-on-windows-10)

I won't be around today but I'll check back when time permits

---

