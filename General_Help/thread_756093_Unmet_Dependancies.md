---
title: "Unmet Dependancies"
date: 2008-04-15
forum: General Help
---

### Post by psycho5 on 2008-04-15
I'm in a real jam over here. 

I am trying to remove awn-curves and install avant from ubuntu repositories, because awn-curves keeps crashing. I manually installed it by using ./configure make and make install. Now I didn't uninstall it before trying to install avant by using apt-get install. I got the following errors:

apt-get install -f 

The following extra packages will be installed:
  libawn0
The following NEW packages will be installed:
  libawn0
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
Need to get 0B/67.2kB of archives.
After unpacking 197kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 157563 files and directories currently installed.)
Unpacking libawn0 (from .../libawn0_0.2.1-0ubuntu1~gutsy1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn0_0.2.1-0ubuntu1~gutsy1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn-bzr
Errors were encountered while processing:
 /var/cache/apt/archives/libawn0_0.2.1-0ubuntu1~gutsy1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
$ 

then i try to remove libawn-bzr

$sudo apt-get remove --purge libawn-bzr

You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  avant-window-navigator: Depends: libawn0 (>= 0.2.1) but it is not going to be installed
  awn-core-applets-bzr: Depends: libawn-bzr but it is not going to be installed
                        Depends: libawn-bzr but it is not going to be installed
  python-libawn-bzr: Depends: libawn-bzr (= 0.2.0-bzr166-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
oj@ubuntupwr:/usr/lib$ 

then i try to remove avant-window-navigator

$sudo apt-get remove --purge avant-window-navigator
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  awn-manager: Depends: avant-window-navigator (>= 0.2)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I try apt-get -f install again It goes back to the error on top... HELP please! :(:confused:

---

### Post by FakeOutdoorsman on 2008-04-15
If you still have the directory that you built awn-curves with you can:
```
cd awn-curves
sudo make uninstall
```

Next time instead of "make install" use checkinstall.  It will create a deb file and add the package to Synaptic, etc.

---

### Post by psycho5 on 2008-04-16
I tried that, still I've got the same error message when doing apt-get install -f

---

### Post by FakeOutdoorsman on 2008-04-16
Try:
```
sudo dpkg --remove --force-remove-reinstreq libawn-bzr
```

---

### Post by psycho5 on 2008-04-16
tried it, i got this output:

dpkg: dependency problems prevent removal of libawn-bzr:
 python-libawn-bzr depends on libawn-bzr (= 0.2.0-bzr166-1).
 awn-core-applets-bzr depends on libawn-bzr.
 awn-core-applets-bzr depends on libawn-bzr; however:
  Package libawn-bzr is to be removed.
 awn-core-applets-bzr depends on libawn-bzr.
 awn-core-applets-bzr depends on libawn-bzr; however:
  Package libawn-bzr is to be removed.
dpkg: error processing libawn-bzr (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 libawn-bzr
$

---

### Post by FakeOutdoorsman on 2008-04-16
```
sudo apt-get autoremove libawn-bzr python-libawn-bzr awn-core-applets-bzr avant-window-navigator
```

This may try to remove other, useful packages.

---

### Post by psycho5 on 2008-04-16
Thanks...

I'll try it once I get home, not near my PC at the moment. 

Hopefully it helps... ty in advance for your help.

I'll post the output in a few hours once i'm done with classes.

---

### Post by psycho5 on 2008-04-17
Hey it worked!


I just had to add an extra awn-manager in the remove list... 


Thanks alot buddy... you really helped me out big time.

---

