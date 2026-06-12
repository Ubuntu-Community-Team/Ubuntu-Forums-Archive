---
title: "Ubuntu Gnome 15.04 Beta 2- Software Center does not open"
date: 2015-04-07
forum: General Help
---

### Post by davilopes-cine on 2015-04-07
[COLOR=#111111][FONT=Ubuntu]It just never opens. I tried every apt related solution. Apt is working fine. Synaptic is working fine. I reinstalled software-center, purged it, and tried to install the lubuntu version.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Nothing works. I really don't want to reinstall the system again :([/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]This is the error that appears in command line:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
```
Traceback (most recent call last): File "/usr/share/software-center/softwarecenter/db/**init**.py", line 4, in from debfile import DebFileApplication, DebFileOpenError File "/usr/share/software-center/softwarecenter/db/debfile.py", line 21, in from apt.debfile import DebPackage File "/usr/lib/python2.7/dist-packages/apt/**init**.py", line 34, in apt_pkg.init_config() SystemError: E:Unable to read /etc/apt/apt.conf.d/ - opendir (13: Permission denied) /usr/share/software-center/softwarecenter/ui/gtk3/SimpleGtkbuilderApp.py:32: Warning: The property GtkImage:stock is deprecated and shouldn't be used anymore. It will be removed in a future version. self.builder.add_from_file(path) /usr/share/software-center/softwarecenter/ui/gtk3/SimpleGtkbuilderApp.py:32: Warning: The property GtkImageMenuItem:use-stock is deprecated and shouldn't be used anymore. It will be removed in a future version. self.builder.add_from_file(path) /usr/share/software-center/softwarecenter/ui/gtk3/SimpleGtkbuilderApp.py:32: Warning: The property GtkImageMenuItem:image is deprecated and shouldn't be used anymore. It will be removed in a future version. self.builder.add_from_file(path) /usr/share/software-center/softwarecenter/ui/gtk3/SimpleGtkbuilderApp.py:32: Warning: The property GtkSettings:gtk-menu-images is deprecated and shouldn't be used anymore. It will be removed in a future version. self.builder.add_from_file(path) /usr/share/software-center/softwarecenter/ui/gtk3/SimpleGtkbuilderApp.py:32: Warning: The property GtkAlignment:top-padding is deprecated and shouldn't be used anymore. It will be removed in a future version. self.builder.add_from_file(path) /usr/share/software-center/softwarecenter/ui/gtk3/SimpleGtkbuilderApp.py:32: Warning: The property GtkAlignment:bottom-padding is deprecated and shouldn't be used anymore. It will be removed in a future version. self.builder.add_from_file(path) /usr/share/software-center/softwarecenter/ui/gtk3/SimpleGtkbuilderApp.py:32: Warning: The property GtkAlignment:left-padding is deprecated and shouldn't be used anymore. It will be removed in a future version. self.builder.add_from_file(path) /usr/share/software-center/softwarecenter/ui/gtk3/SimpleGtkbuilderApp.py:32: Warning: The property GtkAlignment:right-padding is deprecated and shouldn't be used anymore. It will be removed in a future version. self.builder.add_from_file(path) INFO:softwarecenter.ui.gtk3.app:setting up proxy 'None' 2015-04-07 05:56:19,113 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None' Traceback (most recent call last): File "/usr/bin/software-center", line 130, in app = SoftwareCenterAppGtk3(options, args) File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 291, in **init** self.cache = get_pkg_info() File "/usr/share/software-center/softwarecenter/db/pkginfo.py", line 245, in get_pkg_info from softwarecenter.db.pkginfo_impl.aptcache import AptCache File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 39, in class GtkMainIterationProgress(apt.progress.base.OpProgress): AttributeError: 'module' object has no attribute 'progress'
```[/FONT][/COLOR]

---

### Post by kerry_s on 2015-04-07
mine opens just fine. from the looks of your error your missing some ui stuff. software-properties-gtk ?

---

