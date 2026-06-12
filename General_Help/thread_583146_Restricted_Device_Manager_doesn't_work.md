---
title: "Restricted Device Manager doesn't work"
date: 2007-10-20
forum: General Help
---

### Post by Legace on 2007-10-20
I upgraded today from 7.04 Feisty to 7.10 Gutsy.
It's great, but the restricted device manager is NOT working... I would like to uninstall the ATI driver and test the desktop effects :(
When I click on the Restriced Device Manager, you can see "Starting administrative application.." on the taskbar for a second, but the window never shows up..

**-- issue 2 ---**
I also have a bug (?) on the login. When I put the username and password and press enter, it loads the desktop but I see a very old (Windows 2000) fasioned taskbar for a sec, but then my theme loads.. Is this a bug or somethin??

---

### Post by qrdl on 2007-10-20
Try setting LANG=C and running restricted-manager from terminal. Also see [https://bugs.launchpad.net/bugs/154214](https://bugs.launchpad.net/bugs/154214)

---

### Post by Legace on 2007-10-22
This is what it does:

> biru@biru-ubuntu:~$ restricted-manager
  File "/usr/bin/restricted-manager", line 42, in <module>
    rm = RestrictedManager()
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerGtk.py", line 53, in __init__
    RestrictedManagerCommon.__init__(self,args,opts)
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerCommon.py", line 197, in __init__
    self.launch_manager()
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerGtk.py", line 151, in launch_manager
    self.ManagerWindow(self.xml, self.handlers, self)
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerGtk.py", line 209, in __init__
    self.reset_model()
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerGtk.py", line 262, in reset_model
    self.parent.set_title_label(self.xml.get_widget('label_heading'), any_enabled)
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerGtk.py", line 122, in set_title_label
    (bold, normal) = RestrictedManagerCommon.title_label(self, in_use)
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerCommon.py", line 242, in title_label
    'these drivers.') % {'os': get_os_name()}
ValueError: unsupported format character 'k' (0x6b) at index 82


---

