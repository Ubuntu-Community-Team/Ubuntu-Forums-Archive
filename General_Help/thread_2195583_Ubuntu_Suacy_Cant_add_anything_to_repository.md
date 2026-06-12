---
title: "Ubuntu Suacy Cant add anything to repository"
date: 2013-12-25
forum: General Help
---

### Post by tux-world on 2013-12-25
hi all. i want to install KDE 5.
after enter this command:
```
sudo apt-add-repository ppa:kubuntu-ppa/backports
```
i get this error:
```
Traceback (most recent call last):
  File "/usr/bin/apt-add-repository", line 91, in <module>
    sp = SoftwareProperties(options=options)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 109, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 599, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 89, in get_sources
    (self.id, self.codename))
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template for Ubuntu/suacy

```
my content of /etc/lsb-release is :
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.10
DISTRIB_CODENAME=suacy
DISTRIB_DESCRIPTION="Ubuntu 13.10"

```

---

### Post by steeldriver on 2013-12-25
Have you edited your /etc/lsb-release manually at some point? there is a spelling error (s[COLOR=#ff0000]**ua**[/COLOR]cy should be s**au**cy)

---

