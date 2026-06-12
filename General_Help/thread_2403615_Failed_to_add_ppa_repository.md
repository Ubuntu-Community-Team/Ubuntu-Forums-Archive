---
title: "Failed to add ppa repository"
date: 2018-10-13
forum: General Help
---

### Post by jiapei100 on 2018-10-13
```
$ sudo add-apt-repository ppa:videolan/master-daily
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 11, in <module>
    from softwareproperties.SoftwareProperties import SoftwareProperties, shortcut_handler
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 64, in <module>
    from . import shortcuts
  File "/usr/lib/python3/dist-packages/softwareproperties/shortcuts.py", line 23, in <module>
    _DEF_CODENAME = aptsources.distro.get_distro().codename
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 576, in get_distro
    os_release = _OSRelease()
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 529, in __init__
    self.inject_lsb_compat()
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 532, in inject_lsb_compat
    self.result['Distributor ID'] = self.result['ID']
KeyError: 'ID'
```

Did anybody meet the same issue? and how to solve the problem?

Cheers
Pei

---

### Post by oldos2er on 2018-10-13
Which version of Ubuntu?

---

### Post by jiapei100 on 2018-10-14
I'm using Ubuntu 18.04.1

```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:        18.04
Codename:       bionic
```



> **oldos2er said:**
> Which version of Ubuntu?

---

