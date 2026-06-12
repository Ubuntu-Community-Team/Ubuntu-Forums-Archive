---
title: "Wine - Package dependencies cannot be resolved"
date: 2017-05-30
forum: General Help
---

### Post by makem2 on 2017-05-30
Wine has never been installed on the instance of xubuntu. When I use Ubuntu Software Centre to install Wine I get the error:

The following packages have unmet dependencies:


wine1.6: Depends: wine1.6-amd64 (= 1:1.6.2-0ubuntu14) but 1:1.6.2-0ubuntu14 is to be installed
         Depends: binfmt-support (>= 1.1.2) but it is not going to be installed
         Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu14) but it is a virtual package

I am afraid the message does not mean anything to me, can someone guide or does this mean Wine cannot be installed on xubuntu?

All I need in xubuntu is a usable Internet explorer and a working USB port to attach a Chinese ICBC banking dongle for a bank which insists on using Current IE or outdated Firefox. Other than those requirements I don't need Windows.

EDIT: I tried [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu) to install [COLOR=#333333][FONT=Menlo]winehq-devel but again got errors:

[/FONT][/COLOR]```
makem@ssdTOSH:~$ sudo apt-get install --install-recommends winehq-devel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 winehq-devel : Depends: wine-devel (= 2.9.0~xenial)
E: Unable to correct problems, you have held broken packages.
makem@ssdTOSH:~$

```

I do not have any broken packages.

---

### Post by makem2 on 2017-05-30
Solved by checking 'Canconical-supported free and open-source software (main) which was un-checked previously

---

