---
title: "Two great app are not included in Ubuntu [Solved]"
date: 2021-08-31
forum: General Help
---

### Post by al53 on 2021-08-31
Hello there,

I just installed Ubuntu today and I see that it does not have the YouTube GUI, the app in question is: youtube-dlg, nor another app called scid-vs-pc (not scid) it can be downloaded from sourceforge, but not installed here since it is 'proprietary').

How can I get both apps to be installed on Ubuntu?. :(

Thanks.

---

### Post by Dennis N on 2021-08-31
> I see that it does not have the YouTube GUI, the app in question is: youtube-dlg
Did you mean **youtubedl-gui**?

If so, it can be installed as a flatpak.

Also, Ubuntu Repository does offer youtube-dl, which is a command line tool:
```
dmn@Tyana-vm:~$ apt show youtube-dl
Package: youtube-dl
Version: 2020.03.24-1
Priority: extra
Section: universe/web
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>

```
No comment on the other application. Sorry.

---

### Post by QIII on 2021-08-31
As a reminder:  Despite the fact youtube-dl is available in the repos, downloading videos from Youtube isn't something we support here.

Please read [http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955).

---

### Post by grahammechanical on 2021-08-31
If an application or program is described as proprietary it means that the source code is not available for the Ubuntu developers or in fact, anybody to do a code audit on. If the Ubuntu developers are not confident that the software code is safe to use the application will not be included in the Ubuntu repositories.

Having a safe to use operating system and applications is a benefit we get from using an operating system developed and maintained by programmers who believe in Free and Open Source Software (FOSS).

Regards

---

### Post by al53 on 2021-08-31
@ Dennis N

Well, i found this (it is a GUI, which is what i want) but no idea what to do in the last link:

 [https://mrs0m30n3.github.io/youtube-dl-gui/#downloads](https://mrs0m30n3.github.io/youtube-dl-gui/#downloads) [Ubuntu is included]

 

 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/pool/main/y/youtube-dlg/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/pool/main/y/youtube-dlg/)

---

### Post by QIII on 2021-08-31
Again: Despite the fact youtube-dl is available in the repos, downloading videos from Youtube isn't something we support here.

Please read [http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955).

Instructions regarding attempts to install youtube-dl would almost inevitably include some discussion of download testing.

Please take this question elsewhere.

---

### Post by al53 on 2021-08-31
Do you support chess programs? [scid-vs-pc is no included here neither] Thanks.

---

### Post by monkeybrain20122 on 2021-08-31
youtube-dgl is deprecated in any case since it is python2, there is a bundled version in flatpak as said. scidavis has gone closed source and now it is a paid software so it is removed from  the repo and you can only download the old version from source forge

---

### Post by al53 on 2021-08-31
i already found a fork in snap called youtube-dl-pro, it looks ok for now need more ... thanks!

Forgot, there is a fork to in snap for scidvspc > [scidvspc-hkvc]

---

