---
title: "System program problem detected"
date: 2013-05-13
forum: General Help
---

### Post by gramzon on 2013-05-13
Hello.
I installed ubuntu 12.04 LTS and everything worked fine until i installed the AMD drivers. (I have a HD5870)
On the Additional Drivers menu there were 3 options:
Experimental AMD binary Xorg driver and kernel module
ATI/AMD proprietary FGLRX graphics driver (**experimental** beta)
ATI/AMD proprietary FGLRX graphics driver(post-release updates)
I chose to install the post-release updates one and after a reboot i get the purple screen of death.
I looked around to see solutions for this and went to recovery mode, dropped to shell with networking, and tried to do
```
sudo apt-get remove --purge fglrx fglrx-amdcccle
```
but it said something about the package not being installed.
and
```
sudo apt-get remove xorg-drive-fglrx
```
this one gave me a message saying "Virtual packages like xorg-driver-fglrx can't be removed".
Then I did 
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```
and this seems to have done the trick. After reboot I can get into ubuntu.
I tried to install the experimental beta drivers next but they gave me the purple screen of death again.
I removed them with the same command and booted back into ubuntu.

But now every time I get into ubuntu i get a System program problem detected popup.
Details:
```
ExecutablePath
/usr/bin/Xorg
Package
xserver-xorg-core-lts-quantal 2:1.13.0-0ubuntu6.1~precise3
ProblemType
Crash
Title
Xorg crashed with SIGSEGV
ApportVersion
2.0.1-0ubuntu17.2
Architecture
amd64
etc... (cant seem to find a way to copy the whole log)

```

EDIT:
I did this:
```
[COLOR=#333333]sudo apt-get remove --purge xorg-driver-fglrx fglrx*
[/COLOR]sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```
And installed the 13.4 catalyst driver from the amd website and everything seems to work fine now.

---

### Post by deadflowr on 2013-05-13
If you installed the post-release updates then the package would have been
fglrx-updates and not fglrx*.*

---

### Post by fantab on 2013-05-13
Was there an  issue without installing those drivers? How does your machine perform with only the default drivers?

---

### Post by gramzon on 2013-05-14
No it worked fine with the default drivers but I'm not a if it's not broken dont touch if kind of guy :)

---

