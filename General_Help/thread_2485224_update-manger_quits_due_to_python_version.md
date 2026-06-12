---
title: "update-manger quits due to python version"
date: 2023-03-23
forum: General Help
---

### Post by peter67-ubu on 2023-03-23
Recently, the Software Updates window quits when you say yes to installing the latest updates.
The syslog reports the following error.

```
org.debian.apt[4306]:   File "/usr/local/lib/python3.8/dist-packages/pkg_resources/__init__.py", line 2685, in parsed_version
org.debian.apt[4306]:     raise packaging.version.InvalidVersion(f"{str(ex)} {info}") from None
org.debian.apt[4306]: pkg_resources.extern.packaging.version.InvalidVersion: Invalid version: '0.1.36ubuntu1' (package: python-debian)

```

If I run apt-get update; apt-get upgrade, avoiding the GUI, it seems to install the update packages ok.
I was hoping the proper fixes would eventually be imported.  But no luck.

I also searched this before and some recommendations were to modify the python installation version number, or uninstall python-debian, etc.
There was also a note saying this recent code change, causing python to "error out" if the version is incorrect.
But I'm not doing anything special with python installations but it is affecting me.

Do you know when this will be fixed?
And is there a proper work-around?

This error can manifest itself in many different applications.

---

### Post by deadflowr on 2023-03-23
*Thread moved to **General Help***

What version of Ubuntu?

---

