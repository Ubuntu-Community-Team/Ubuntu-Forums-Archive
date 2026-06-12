---
title: "Problem adding resources"
date: 2012-11-18
forum: General Help
---

### Post by c5wagner on 2012-11-18
I can't add new resources. It won't work on synaptic or via terminal and any help would be appreciated. Happens with any source i try adding.
```
$ sudo add-apt-repository ppa:kilian/f.lux
[sudo] password for chad: 
You are about to add the following PPA to your system:
 PPA for the f.lux indicator applet
 More info: https://launchpad.net/~kilian/+archive/f.lux
Press [ENTER] to continue or ctrl-c to cancel adding it

Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 160, in <module>
    sp = SoftwareProperties(options=options)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 96, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 584, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.7/dist-packages/aptsources/distro.py", line 87, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

```
Edit: problem fixed, I reinstalled my update manager

---

