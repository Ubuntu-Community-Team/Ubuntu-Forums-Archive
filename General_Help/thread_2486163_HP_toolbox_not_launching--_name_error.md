---
title: "HP toolbox not launching-- name error"
date: 2023-04-21
forum: General Help
---

### Post by nah40 on 2023-04-21
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

QSocketNotifier: Can only be used with threads started with QThread
Traceback (most recent call last):
  File "/usr/bin/hp-toolbox", line 280, in <module>
    toolbox = ui.DevMgr5(__version__, device_uri,  None)
              ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/share/hplip/ui5/devmgr5.py", line 238, in __init__
    core =  CoreInstall(MODE_CHECK)
            ^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/share/hplip/installer/core_install.py", line 240, in __init__
    self.passwordObj = password.Password(ui_mode)
                       ^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/share/hplip/base/password.py", line 94, in __init__
    self.__readAuthType()  # self.__authType
    ^^^^^^^^^^^^^^^^^^^^^
  File "/usr/share/hplip/base/password.py", line 119, in __readAuthType
    distro_name = get_distro_std_name(os_name)
                  ^^^^^^^^^^^^^^^^^^^
NameError: name 'get_distro_std_name' is not defined. Did you mean: 'get_distro_name'?

---

