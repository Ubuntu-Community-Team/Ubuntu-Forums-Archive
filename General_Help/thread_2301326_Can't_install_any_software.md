---
title: "Can't install any software"
date: 2015-11-01
forum: General Help
---

### Post by fisheye11 on 2015-11-01
I'm running 15.10, but I can't install any new programs with the software center.  Everytime, I get the same error:

"Software can't be installed or removed because the authentication service is not available. (org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.143'}): org.debian.apt.install-or-remove-packages"

What should I do?

---

### Post by DK1993 on 2015-11-01
I would reinstall the Software Center in terminal.

```
[COLOR=#111111][FONT=Consolas]sudo apt-get update[/FONT][/COLOR]
```
This will update the repositories before reinstalling the Software Center.

Then paste this into Terminal:
```
[COLOR=#111111][FONT=Consolas]sudo apt-get --purge --reinstall install software-center software-properties-common software-properties-gtk[/FONT][/COLOR]
```

See if this helps you out and if it solves the problem. If not get back to us.

---

### Post by RobGoss on 2015-11-01
Hello and welcome, is this a new install of 15.10 if it is sometimes it best to reinstall it again to avoid lost time trying to figure what's causing the problem that's if you don't have much to loose

---

