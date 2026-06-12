---
title: "[SOLVED] Skype on 64bit 13.04"
date: 2013-04-26
forum: General Help
---

### Post by timgood on 2013-04-26
There is a problem with Skype and NVidia and (I believe) some ATI drivers which causes a segmentation fault when launched. This workaround fixes it:
```
sudo -s
mv /usr/bin/skype /usr/bin/skype-bin
gedit /usr/bin/skype
```

then copy this:
```
#!/bin/sh
export LD_PRELOAD=/usr/lib/i386-linux-gnu/mesa/libGL.so.1
exec skype-bin
```

save and close and then:
```
chmod 0755 /usr/bin/skype
```

However I am still getting issues with Skype running 64bit 13.04

The notification icon does not show. sni-qt is installed.
Sound output is set to default audio output, but can not be muted. Everything else will mute, but Skype notifications continue to boom out.

Help would be gratefully received!

---

### Post by timgood on 2013-04-28
bump...

---

### Post by timgood on 2013-04-29
I uninstalled skype and then added the partner repositories and installed from there. It pulled down a few more dependencies. Then following the instructions [here]("http://www.webupd8.org/2013/04/fix-s...untu-1304.html") I managed to get it working correctly and the icon has appeared and sound is back to normal.

---

### Post by LinuXXuniL on 2013-04-29
I've created the file in * /usr/local/bin*, added *sudo chmod +x skype*.

Instaled skype with following commands:

[I]sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"
sudo apt-get update && sudo apt-get install skype[/I]

Now it's working.

---

### Post by monkeybrain2012 on 2013-04-30
Today's Skype update solves the problem.

---

### Post by Jovanontherun on 2013-05-31
@timgood
There is no longer page you've shared

---

