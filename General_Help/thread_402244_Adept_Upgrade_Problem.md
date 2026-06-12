---
title: "Adept Upgrade Problem"
date: 2007-04-05
forum: General Help
---

### Post by toran on 2007-04-05
OK, so I tried to update all the packages on my system with adept; a routine operation that usually works without any problems.

Today when I tried to upgrade everything, however, one package would not upgrade without problems: adept-common. I tried upgrading it from the console, which gave me back more information about the problem:

```

jon@gimli:~$ aptitude install adept-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  adept-common
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 96.5kB of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  adept-common: Depends: konsole (>= 4:3.5.5-0ubuntu3.3) but 4:3.5.5-0ubuntu3.2 is installed.
                Depends: python-kde3 (>= 3.15.2+20060422-2ubuntu4.3) but 3.15.2+20060422-2ubuntu4 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
adept
adept-batch
adept-common
adept-installer
adept-manager
adept-notifier
adept-updater
kubuntu-desktop
language-selector-qt

Score is -3109

Accept this solution? [Y/n/q/?] n
Resolving dependencies...

*** No more solutions available ***

The following actions will resolve these dependencies:

Remove the following packages:
adept
adept-batch
adept-common
adept-installer
adept-manager
adept-notifier
adept-updater
kubuntu-desktop
language-selector-qt

Score is -3109

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
jon@gimli:~$
```

can someone please help me?

thanks

---

### Post by abloylas on 2007-04-06
I had the same problem last night and filed a bug report on [https://bugs.launchpad.net/ubuntu/+source/adept/+bug/103414](https://bugs.launchpad.net/ubuntu/+source/adept/+bug/103414)
Maybe you could give some more information to the guys there.

---

### Post by abloylas on 2007-04-06
The problem has been fixed. Try upgrading again.

---

