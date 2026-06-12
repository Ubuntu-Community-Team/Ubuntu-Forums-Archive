---
title: "unable to start genymotion"
date: 2014-02-22
forum: General Help
---

### Post by jrmchess on 2014-02-22
I have kde on ubuntu and have successfully installed genymotion but I am unable to start it. Whenever I try to launch it from the genymotion folder using ```
./genymotion
``` I get the message 

> Installing log handler
Logging activities to file: /home/****
Aborted (core dumped)


Can u please help? Thanks

---

### Post by jrmchess on 2014-02-23
Hi,

I want to run an android emulator on ubuntu. Any help??? 


Thanks

---

### Post by llamabr on 2014-02-23
The instructions say you need GLEW.  Did you install it?  Try:

```
sudo apt-get install Xmu-dev Xi-Dev
```


[http://glew.sourceforge.net/build.html](http://glew.sourceforge.net/build.html)
[https://cloud.genymotion.com/page/faq/](https://cloud.genymotion.com/page/faq/)

---

### Post by jrmchess on 2014-02-24
> **llamabr said:**
> The instructions say you need GLEW.  Did you install it?  Try:

```
sudo apt-get install Xmu-dev Xi-Dev
```


[http://glew.sourceforge.net/build.html](http://glew.sourceforge.net/build.html)
[https://cloud.genymotion.com/page/faq/](https://cloud.genymotion.com/page/faq/)

when I try to install it, it says > E: Unable to locate package Xmu-dev
E: Unable to locate package Xi-Dev

---

### Post by jrmchess on 2014-02-25
I checked the genymotion.log and got this:




> Feb 22 23:06:31 [Genymotion] [Warning] ****  STARTING GENYMOTION  **** 
Feb 22 23:06:31 [Genymotion] [Warning] Genymotion Version: Genymotion 2.1.1 
Feb 22 23:06:32 [Genymotion] [Debug] Got bus address:  "unix:abstract=/tmp/dbus-BQtwFlbfO9,guid=25baa36995e968fee2248b680000002e" 
Feb 22 23:06:32 [Genymotion] [Debug] Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-BQtwFlbfO9,guid=25baa36995e968fee2248b680000002e" 
Feb 22 23:06:32 [Genymotion] [Debug] Registered DEC:  true 
Feb 22 23:06:32 [Genymotion] [Debug] Proxy configuration: no proxy used 
Feb 22 23:06:32 [Genymotion] [Debug] Network request to URL:  "https://cloud.genymotion.com/launchpad/last_version/linux/x86/" 
Feb 22 23:12:55 [Genymotion] [Fatal] Cannot mix incompatible Qt library (version 0x40801) with this library (version 0x40804)
Feb 22 23:20:58 [Genymotion] [Fatal] Cannot mix incompatible Qt library (version 0x40801) with this library (version 0x40804)
Feb 24 00:10:53 [Genymotion] [Fatal] Cannot mix incompatible Qt library (version 0x40801) with this library (version 0x40804)
Feb 24 00:15:13 [Genymotion] [Fatal] Cannot mix incompatible Qt library (version 0x40801) with this library (version 0x40804)
Feb 25 23:01:00 [Genymotion] [Fatal] Cannot mix incompatible Qt library (version 0x40801) with this library (version 0x40804)
Feb 26 00:00:31 [Genymotion] [Fatal] Cannot mix incompatible Qt library (version 0x40801) with this library (version 0x40804)

Any ideas?

---

### Post by earruda on 2014-06-12
I have fixed this issue doing the following:
1 - Installing the libs:
```
# apt-get install libxi-dev libxmu-dev
```

2 - (Re)Moving the Qt libs inside the Genymotion installation directory
```
mkdir QtLibs && mv *Qt*.so* QtLibs
```

This last command will make Genymotion use the system's Qt libs.

Hope this works for you.

---

### Post by danielzazen on 2014-06-25
> **verton_Arruda said:**
> I have fixed this issue doing the following:
1 - Installing the libs:
```
# apt-get install libxi-dev libxmu-dev
```

2 - (Re)Moving the Qt libs inside the Genymotion installation directory
```
mkdir QtLibs && mv *Qt*.so* QtLibs
```

This last command will make Genymotion use the system's Qt libs.

Hope this works for you.

Made that and got "Segment Violation" and no log in HOME/.Genymobile/genymotion.log
Any ideas?

---

### Post by kokwak on 2015-02-14
that works! thanks alot!

---

