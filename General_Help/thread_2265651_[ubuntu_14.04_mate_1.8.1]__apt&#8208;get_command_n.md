---
title: "[ubuntu 14.04 mate 1.8.1]  apt&#8208;get: command not found"
date: 2015-02-16
forum: General Help
---

### Post by aris5 on 2015-02-16
Hello guys, i am trying to install gns from this [guide]("http://www.computingforgeeks.com/2015/02/easiest-way-to-install-gns3-123-on.html").
After many distribution changes this last month i ended up using Ubuntu mate - everything works fine, skype, camera, printer , hdmi - i don't want to change distribution.

But i cannot use the command "[COLOR=#363231][FONT=Open Sans Condensed]sudo apt&#8208;get install xxx[/FONT][/COLOR]" - it fails with  "sudo: apt&#8208;get: command not found" and i cannot install anything.

The strange think is in these 3 commands are working:
```
[COLOR=#363231][FONT=Open Sans Condensed]sudo apt-get update[/FONT][/COLOR]
[COLOR=#363231][FONT=Open Sans Condensed]sudo apt-get upgrade[/FONT][/COLOR]
[COLOR=#363231][FONT=Open Sans Condensed]sudo apt-get dist-upgrade[/FONT][/COLOR]
```

but all the other commands are failing with "sudo: apt&#8208;get: command not found - what can i do please?

```
[COLOR=#363231][FONT=Open Sans Condensed]Then fix the missing dependencies needed for GNS3 installation.[/FONT][/COLOR][INDENT] sudo apt&#8208;get install python3&#8208;zmq
 sudo apt&#8208;get install python3&#8208;tornado
 sudo apt&#8208;get install python3&#8208;netifaces
 sudo apt&#8208;get install python3&#8208;setuptools
 sudo apt&#8208;get install python3&#8208;pyqt4
 sudo apt&#8208;get install python3&#8208;ws4py[/INDENT]
[COLOR=#363231][FONT=Open Sans Condensed]Now install the following Dependencies needed by Dynamips hypervisor.[/FONT][/COLOR][INDENT]  sudo apt&#8208;get install uuid&#8208;dev
  sudo apt-get install cmake 
  sudo apt&#8208;get install libelf&#8208;dev
  sudo apt&#8208;get install libpcap&#8208;dev[/INDENT]


```

which apt-get is returning /usr/bin/apt-get and apt-get is /usr/bin/apt-get.
Thank you for your suggestions.

---

### Post by steeldriver on 2015-02-16
Are you actually typing the commands, or did you copy-pate them from a website? sometimes non-ascii characters can sneak in: in this case it looks like the '-' in apt-get is actually E2 80 90 &dash

---

