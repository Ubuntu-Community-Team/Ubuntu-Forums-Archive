---
title: "apt fully broken cant find a fix"
date: 2007-11-20
forum: General Help
---

### Post by neoroses on 2007-11-20
hey guys i have fully nakerd my apt....i have read every post there is and still cannot fix it, i did a bad install of somthing, dcp130ccupswrapper, and now every time i go to use apt or the package manager i get this error:

```
E: The package dcp130ccupswrapper needs to be reinstalled, but I can't find an archive for it.

```

and i CANNOT  fix this error so it has pretty much crippled me :( please help lads i think i have had a good look around already but no joy

---

### Post by por100pre1 on 2007-11-20
You could need to remove it, like this:

```
sudo dpkg --remove --force-remove-reinstreq dcp130ccupswrapper
```

---

### Post by neoroses on 2007-11-20
thanks for fast reply...but alredy tryed that dude no joy:(

```
 sudo dpkg --remove --force-remove-reinstreq dcp130ccupswrapper
[sudo] password for ben:
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 94785 files and directories currently installed.)
Removing dcp130ccupswrapper ...
/var/lib/dpkg/info/dcp130ccupswrapper.prerm: 3: /usr/local/Brother/Printer/dcp130c/cupswrapper/cupswrapperdcp130c: not found
dpkg: error processing dcp130ccupswrapper (--remove):
 subprocess pre-removal script returned error exit status 127
/var/lib/dpkg/info/dcp130ccupswrapper.postinst: 3: /usr/local/Brother/Printer/dcp130c/cupswrapper/cupswrapperdcp130c: not found
cp: cannot stat `/usr/share/cups/model/brdcp130c.ppd': No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dcp130ccupswrapper

```

---

### Post by dancingfoot on 2008-06-11
Hi i have the same problem 

were you able to fix it?

---

