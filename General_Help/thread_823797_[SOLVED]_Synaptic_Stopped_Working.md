---
title: "[SOLVED] Synaptic Stopped Working"
date: 2008-06-09
forum: General Help
---

### Post by Gannon8 on 2008-06-09
I wanted to use KDE with ubuntu with GNOME, so I used
```
sudo apt-get install kubuntu-desktop kde-core
```To install it. But it cluttered my applications menu horribly, so I uninstalled it using
```
sudo apt-get remove kubuntu-desktop kde-core
```
Seeing as that removed 2 packages out of the many that apt-get installed for me, I used
```
sudo apt-get remove kde*
```as well as autoremove. Now I can't get into synaptic, I get the attached error message.

Everything in /etc/apt/sources.list looks normal. I have updated using apt-get and here's what happened when I used apt-get remove -f:
```
gannon8@g8-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kio-umountwrapper
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 111kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 123138 files and directories currently installed.)
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Gannon8 on 2008-06-09
Ok, Never mind. Running synaptic-update installed a few missing packages and fixed synaptic.

---

