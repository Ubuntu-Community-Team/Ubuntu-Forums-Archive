---
title: "dpkg: error processing... E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2013-02-21
forum: General Help
---

### Post by lprofil on 2013-02-21
Hello,

i would appreciate if somebody could help me with this problem
which occured trying to install the package qt4-default:

```
user@machine:~$ sudo apt-get install qtchooser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  qt4-default
The following NEW packages will be installed:
  qtchooser
0 upgraded, 1 newly installed, 0 to remove and 130 not upgraded.
90 not fully installed or removed.
Need to get 0 B/15.1 kB of archives.
After this operation, 73.7 kB of additional disk space will be used.
(Reading database ... 204619 files and directories currently installed.)
Unpacking qtchooser (from .../qtchooser_0.0.1~git20121229.g8f08405-0ubuntu1~precise1~test5_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/qtchooser_0.0.1~git20121229.g8f08405-0ubuntu1~precise1~test5_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/qdbusxml2cpp', which is also in package libqt4-dev 4:4.8.1-0ubuntu4.4
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/qtchooser_0.0.1~git20121229.g8f08405-0ubuntu1~precise1~test5_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Tanks in advance.

/lprofil

---

### Post by dino99 on 2013-02-21
qtchooser is a RR package, are you using raring ?
if you also use some ppa(s), then it can be a conflict (needing ppa-purge)

you can try to clean: clean/autoclean/autoremove, then re-upload

or download from lp:  [https://launchpad.net/ubuntu/+source/qtchooser](https://launchpad.net/ubuntu/+source/qtchooser)
and force installation by: sudo dpkg -i qtch*

---

### Post by lprofil on 2013-02-21
Hello Dino,

thanks for the quick reply. I forgot to mention my system:
it is a 12.04-amd64 version.

And yes, i tried to install the package through [this ppa respo]("http://developer.ubuntu.com/get-started/gomobile/").
And indead: your are right. Trying to install a raring package on a precise system might not be the best of ideas.
Unfortunately there seems to be no alternative than running the
devel enviroment on a 13.04 system - which i a setting up right now.

Thanks again for your help.

/lprofil

---

### Post by schragge on 2013-02-21
> **dino99 said:**
> and force installation by: sudo dpkg -i qtch*Well, simple *dpkg -i* is not enough in this case, since the file in question already owned by another installed package. You have two options
[list]
[*] First, uninstall *libqt4-dev*. *sudo apt-get remove* probably won't work, since apt-get can attempt to install qtchooser first and will fail again. Rather try ```
sudo dpkg -r libqt4-dev
``` Then try to install *qtchooser* again. Quite possible, you'll also need to uninstall qt-sdk.
[*]Force dpkg to overwrite the file owned by *libqt4-dev* with the file from *qtchooser*. Not the best idea, for sure, but sometimes you don't have the choice. To do this, run
```

sudo apt-get clean
sudo apt-get -d --no-upgrade install qtchooser
sudo dpkg --force-overwrite -i /var/cache/apt/archive/qtch*.deb

```
[/list]

---

### Post by hkw on 2013-02-23
> **lprofil said:**
> Hello,

i would appreciate if somebody could help me with this problem
which occured trying to install the package qt4-default:

```
user@machine:~$ sudo apt-get install qtchooser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  qt4-default
The following NEW packages will be installed:
  qtchooser
0 upgraded, 1 newly installed, 0 to remove and 130 not upgraded.
90 not fully installed or removed.
Need to get 0 B/15.1 kB of archives.
After this operation, 73.7 kB of additional disk space will be used.
(Reading database ... 204619 files and directories currently installed.)
Unpacking qtchooser (from .../qtchooser_0.0.1~git20121229.g8f08405-0ubuntu1~precise1~test5_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/qtchooser_0.0.1~git20121229.g8f08405-0ubuntu1~precise1~test5_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/qdbusxml2cpp', which is also in package libqt4-dev 4:4.8.1-0ubuntu4.4
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/qtchooser_0.0.1~git20121229.g8f08405-0ubuntu1~precise1~test5_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```Tanks in advance.

/lprofil

[[COLOR=#000000]Hi lprofil[/COLOR]]("http://ubuntuforums.org/member.php?u=11491") (and to the Ubuntu Forum)

Had this issue too. Are you running Sputnik and trying to install the ubuntu-sdk?

Tried a few things and I looked on here but I think al that fixed it was:
 
```
sudo apt-get remove qt5-default ubuntu-sdk
```

Hope that helps.

---

