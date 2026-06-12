---
title: "openoffice.org and ubuntu-desktop dependancy issue for uninstall"
date: 2006-12-23
forum: General Help
---

### Post by Burgresso on 2006-12-23
I wanted to uninstall openoffice.org but I'm getting a disheartening error:
```

me@mycomputer:~$ sudo aptitude remove openoffice.org
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  ubuntu-desktop 
The following packages will be REMOVED:
  openoffice.org 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 28.7kB will be freed.
The following packages have unmet dependencies:
  ubuntu-desktop: Depends: openoffice.org but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-desktop

Score is -301

Accept this solution? [Y/n/q/?]

```

How should I proceed? Does this mean that removing OO will break the installation?

thanks

burgresso

---

### Post by dcstar on 2006-12-23
> **Burgresso said:**
> I wanted to uninstall openoffice.org but I'm getting a disheartening error:
.......
How should I proceed? Does this mean that removing OO will break the installation?

thanks

burgresso

No, "ubuntu-desktop" is a meta-package that just contains all of the default apps.

There are numerous posts in the forum on this exact issue, if you want more info do a search for them.

---

### Post by blackmh on 2006-12-23
It won't

---

