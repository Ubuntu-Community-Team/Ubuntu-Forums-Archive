---
title: "how to force an uninstall"
date: 2006-11-09
forum: General Help
---

### Post by Moosferatu on 2006-11-09
I was attempting to compile and install an older version of wine, but it failed and I'm now having trouble completely removing it from my computer.  I've tried

```
sudo make uninstall
``` 

```
sudo dpkg -r wine -- purge --force-all
```

and installing the current version of wine from Synaptic over it.  But none of this has seemed to get rid of it.

```
sudo dpkg -r wine -- purge --force-all
```

gives me:

```
(Reading database ... 147920 files and directories currently installed.)
Removing wine ...
dpkg - warning: ignoring request to remove -- which isn't installed.
dpkg - warning: ignoring request to remove purge which isn't installed.
dpkg - warning: ignoring request to remove --force-all which isn't installed.
```

and

```
dpkg -l wine
```

gives me this:

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
rc  wine           0.9.24~winehq0 Microsoft Windows Compatibility Layer (Binar

```

Any ideas?

---

