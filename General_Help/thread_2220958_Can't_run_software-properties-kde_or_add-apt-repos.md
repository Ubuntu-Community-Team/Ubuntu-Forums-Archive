---
title: "Can't run software-properties-kde or add-apt-repository"
date: 2014-04-30
forum: General Help
---

### Post by nos-developer on 2014-04-30
I am using Kubuntu 14.04 and I can't run sudo add-apt-repository or sudo software-properties-kde. I get the following traceback message:

```
Traceback (most recent call last):
  File "/usr/bin/software-properties-kde", line 136, in <module>
    app = SoftwarePropertiesKDE(datadir=data_dir, options=options, file=afile, attachWinID=attachWinID)
  File "/usr/lib/python3/dist-packages/softwareproperties/kde/SoftwarePropertiesKDE.py", line 64, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 103, in __init__
    self.sourceslist = SourcesList()
  File "/usr/lib/python3/dist-packages/aptsources/sourceslist.py", line 274, in __init__
    self.matcher = SourceEntryMatcher(matcherPath)
  File "/usr/lib/python3/dist-packages/aptsources/sourceslist.py", line 459, in __init__
    dist = DistInfo(f, base_dir=matcherPath)
  File "/usr/lib/python3/dist-packages/aptsources/distinfo.py", line 186, in __init__
    for line in dist_file:
  File "/usr/lib/python3.4/codecs.py", line 313, in decode
    (result, consumed) = self._buffer_decode(data, self.errors, final)
UnicodeDecodeError: 'utf-8' codec can't decode byte 0xae in position 2: invalid start byte
```

I have reported it as a bug but apparently it isn't a bug. How can I fix this

Bug report: [https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1312540](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1312540)

---

### Post by ian-weisser on 2014-04-30
Looks to me like it was accepted as a valid bug.
Status is NEW instead of CLOSED or REJECTED

---

### Post by vasa1 on 2014-04-30
> **nos-developer said:**
> I am using Kubuntu 14.04 ...
Bug report: [https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1312540](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1312540)
but in the bug you say that "I am using Software-Properties-KDE version 0.92.36 on ubuntu 14.04 LTS with some optional kde components installed (ie. Not kubuntu-desktop)."

So you're not using Kubuntu 14.04?

---

