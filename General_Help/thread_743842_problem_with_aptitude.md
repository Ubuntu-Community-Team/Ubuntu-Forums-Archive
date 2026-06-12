---
title: "problem with aptitude"
date: 2008-04-03
forum: General Help
---

### Post by vizitorq on 2008-04-03
for some reason, some of my apps won't install. and i've diagnosed the problem to have something to do with python-setuptools.

```
kumi@throne:~ % sudo apt-get install python-setuptools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-setuptools is already the newest version.
The following packages were automatically installed and are no longer required:
  anyevent-perl vim-gui-common libevent-perl libevent-rpc-perl devhelp-common
  libfame-0.9 libqof1 libquicktime0 dictzip libanyevent-perl libgsf0.0-cil
  libpvm3 gtk2-ex-formfactory-perl wireshark-common kicker libxfcegui4-4
  libfile-desktopentry-perl libavcodec0d libevent-execflow-perl mplayer-skins
  libassa3.4-0 libkonq4 libwv-1.2-3 liferea-mozilla ogmtools
  libfile-basedir-perl libtranslate0 dictd libdevhelp-1-0 libpostproc0d
  transcode libdc1394-13 libxfce4util4 libfile-mimeinfo-perl libmjpegtools0c2a
  libintl-perl kdebase-data libadns1 libimlib2 mzscheme
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up python-setuptools (0.6c5-1ubuntu1) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/setuptools.pth
pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/setuptools.pth
dpkg: error processing python-setuptools (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-setuptools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

any suggestions?

---

### Post by kesman on 2008-04-03
well first clean that mess up with
```

sudo apt-get autoremove

```
then
```

sudo apt-get update
sudo apt-get install --reinstall python-setuptools

```
maybe this fixes your problem.

---

### Post by vizitorq on 2008-04-03
i knew there was a problem because when i used the add/remove feature to add some apps, it brought up an error for some of them:

an error occured: E: python-setuptools: subprocess post-installation script returned error exit status 1

so i don't know what that means, but i just tried to install python-setuptools, and it says that everything's ok... so i don't know what the deal is. does anybody have any idea what could be going on here?

---

### Post by kesman on 2008-04-03
Did you get errors with the commands I gave you?

---

### Post by vizitorq on 2008-04-03
when i sudo apt-get autoremove, at the end, it gives me this:

```
Removing libxfce4util4 ...
Removing liferea-mozilla ...
Removing mplayer-skins ...
Removing mzscheme ...
Removing ogmtools ...
Removing vim-gui-common ...
Setting up python-setuptools (0.6c5-1ubuntu1) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/setuptools.pth
pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/setuptools.pth
dpkg: error processing python-setuptools (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-setuptools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

what doe sthat mean? is that ok, or bad?

---

### Post by kesman on 2008-04-03
Well try this first:
```

sudo apt-get install --reinstall python-setuptools

```
if it fails, do
```

sudo apt-get purge python-setuptools && sudo apt-get update && sudo apt-get install python-setuptools

```

---

### Post by vizitorq on 2008-04-03
yeah it works. you da man!!!!

---

### Post by kesman on 2008-04-03
Maybe mark the thread solved now?

---

### Post by mezhaka on 2008-06-21
thanks kesman.
i was getting the following:
```

pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing python-setuptools (--configure):
 subprocess post-installation script returned error exit status 1

```
and your second suggestion solved the problem:
> 
```

sudo apt-get purge python-setuptools && sudo apt-get update && sudo apt-get install python-setuptools

```

---

