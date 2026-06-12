---
title: "Software-center doesn't work"
date: 2012-10-23
forum: General Help
---

### Post by jas88 on 2012-10-23
Hi, i have version 10.04 of Ubuntu, *Lucid Lynx*, and when I run the software-center from menu -> Applications looks set to open in the taskbar, but after a few seconds disappears and does not open. Running it from the shell I get the following:


```
software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 78, in 
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 44, in 
    from view.installedpane import InstalledPane
  File "/usr/share/software-center/softwarecenter/view/installedpane.py", line 33, in 
    from softwarepane import SoftwarePane, wait_for_apt_cache_ready
  File "/usr/share/software-center/softwarecenter/view/softwarepane.py", line 37, in 
    from appdetailsview import AppDetailsView
  File "/usr/share/software-center/softwarecenter/view/appdetailsview.py", line 50, in 
    from widgets.imagedialog import ShowImageDialog, GnomeProxyURLopener, Url404Error, Url403Error
  File "/usr/share/software-center/softwarecenter/view/widgets/imagedialog.py", line 19, in 
    import gconf
ImportError: No module named gconf
```

---

### Post by mag1strate on 2012-10-23
Have you tried re-installing software center?

Open the terminal and type the following:

[PHP]sudo dpkg -r software-center[/PHP]

Then do the following:

[PHP]sudo apt-get install software-center[/PHP]

---

### Post by jas88 on 2012-10-24
> **mag1strate said:**
> Have you tried re-installing software center?

Open the terminal and type the following:

[PHP]sudo dpkg -r software-center[/PHP]

Then do the following:

[PHP]sudo apt-get install software-center[/PHP]

Yes, I've tried that and still doesn't work, I've also tried to upgrade and update

---

### Post by mag1strate on 2012-10-24
I believe gconf has to do with python and gnome. You might need to get some dependencies or reinstall those files.

---

### Post by jas88 on 2012-10-24
> **mag1strate said:**
> I believe gconf has to do with python and gnome. You might need to get some dependencies or reinstall those files.

I reinstalled several gnome libraries and python libraries and it works. Thank you

---

### Post by since on 2012-10-24
LOL

use apt-get instead!

---

### Post by mag1strate on 2012-10-24
Glad that helped!

---

