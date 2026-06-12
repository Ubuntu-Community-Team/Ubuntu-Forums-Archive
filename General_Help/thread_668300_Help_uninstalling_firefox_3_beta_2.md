---
title: "Help uninstalling firefox 3 beta 2"
date: 2008-01-15
forum: General Help
---

### Post by andy_hubb on 2008-01-15
Hi,

I installed firefox 3 beta 2 using the instructions at:
[http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html)

As I can't get flash or java to work in firefox 3, I want to be able to revert back to firefox 2 but the instructions replaced all the firefox launchers with firefox 3.

I'd appreciate any help,

cheers

---

### Post by cdenley on 2008-01-15
You could try this
```

sudo aptitude reinstall firefox

```

---

### Post by ~LoKe on 2008-01-15
How about starting with a thread to fix your plugin issues?

---

### Post by jrusso2 on 2008-01-15
Plugins work fine here with Firefox 3 beta 3 and its a nice browser.  Uses a lot less memory then Firefox 2 and it seems a bit snappier.

When its done its going to be real sweet.

---

### Post by andy_hubb on 2008-01-15
cheers,  ill try and get the plugins to work first then

---

### Post by Badjaccur on 2008-01-18
I managed to roll back to Firefox 2 by doing:

```

$ sudo rm /usr/bin/firefox
$ sudo rm /opt/firefox
$ sudo dpkg-divert --rename --remove /usr/bin/firefox
$ sudo apt-get install firefox --reinstall

```
I will wait for the official Firefox 3 release. I looking forward to it but I can not stand a minute without AdBlock.

---

