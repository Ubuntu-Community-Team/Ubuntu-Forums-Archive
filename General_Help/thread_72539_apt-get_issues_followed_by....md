---
title: "apt-get issues followed by..."
date: 2005-10-06
forum: General Help
---

### Post by sd_ap on 2005-10-06
So the default sources.list file given to me from hoary's install, any/all apt-get install &packagename resulted in the same...cannot be found.

after reading some posts, i substituded my sources.list file with the one from the guide.  Then the backports were causing 404s.  I again dug for some fixes and finally found something that doesnt give me errors when i apt-get update.  My current sources.list file allows me to update, and my package manager once again let me know that I had some packages to update.  yipee!

Below is my sources.list in case it is needed:
```

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


##Archives res/universe/multiverse
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe
deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

##Security res/universe
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted
deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

## Backports
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted

```

now, i am going through the guide and felt like checking out some programs...first was the gnome menu editor...

```

gibson@smurf:/etc/apt$ sudo apt-get install smeg
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  smeg: Depends: python-xdg (>= 0.14) but 0.9-1 is to be installed
E: Broken packages
gibson@smurf:/etc/apt$

```

python errors...odd.  so I went to install python-xdg for kicks..

```

gibson@smurf:/etc/apt$ sudo apt-get install python-xdg
Reading package lists... Done
Building dependency tree... Done
python-xdg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gibson@smurf:/etc/apt$

```

sooooo how do i install smeg?  

this is not the first application that has given me issues, but I think it is time to see what exactly is going on here... :)

any help is greatly appreciated!  I am going to forge forward with the other things I wanted to play with and as they give me errors, I am going to toss them in replies as sort of a log...

Cheers!
-Sean

---

### Post by Tinwood on 2005-10-07
You are running Hoary?

The version of python-xdg that is currently in Hoary is 0.9-1 as shown in your post. However, smeg wants a version of python-xdg >= 0.14 - i.e. newer than you have.

smeg seems to come from backports:

```

# apt-cache showpkg smeg
Package: smeg
Versions:
0.7.5-0ubuntu1~hoary1(/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-backports_universe_binary-i386_Packages)

Reverse Depends:
Dependencies:
0.7.5-0ubuntu1~hoary1 - python (2 2.4) python2.4-gtk2 (2 2.6) python2.4-libxml2 (2 2.6.17) python-xdg (2 0.14) python2.4-glade2 (2 2.6) gnome-menus (18 2.10) kdelibs-data (2 3.4) menueditor (0 (null))
Provides:
0.7.5-0ubuntu1~hoary1 -
Reverse Provides:

``` 
However, then it gets a bit weird because apt-show-versions -a python-xdg gives:

```

python-xdg      0.14-0ubuntu1~5.04ubp1  install ok installed
python-xdg      0.14-0ubuntu1~5.04ubp1  unknown
python-xdg/unknown uptodate 0.14-0ubuntu1~5.04ubp1

``` 
and apt-cache show python-xdg gives:
```

Package: python-xdg
Status: install ok installed
Priority: optional
Section: python
Installed-Size: 216
Maintainer: Sebastien Bacher <seb128@debian.org>
Architecture: all
Source: pyxdg
Version: 0.14-0ubuntu1~5.04ubp1
Depends: python (<< 2.5), python (>= 2.4)
Description: A python library to access freedesktop.org standards
 PyXDG contains implementations of freedesktop.org standards in python:
 .
  * Base Directory Specification Version 0.6
  * Menu Specification Version 0.6
  * Desktop Entry Specification Version 0.9.4
  * Icon Theme Specification Version 0.7

Package: python-xdg
Priority: optional
Section: python
Installed-Size: 164
Maintainer: Sebastien Bacher <seb128@debian.org>
Architecture: all
Source: pyxdg
Version: 0.9-1
Depends: python (<< 2.5), python (>= 2.4)
Filename: pool/main/p/pyxdg/python-xdg_0.9-1_all.deb
Size: 20394
MD5sum: 1ca78a5bf8b36199399448f66c39b6fc
Description: A python library to access freedesktop.org standards
 PyXDG contains implementations of freedesktop.org standards in python:
 .
  * Base Directory Specification Version 0.6
  * Menu Specification Version 0.6
  * Desktop Entry Specification Version 0.9.4
  * Icon Theme Specification Version 0.7
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop

``` 

WARNING - the next bit I said is probably wrong!

> 
The reason I say 'wierd' is because apt-cache showpkg python-xdg gives:
```

Package: python-xdg
Versions:
0.14-0ubuntu1~5.04ubp1(/var/lib/dpkg/status)
0.9-1(/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages)

Reverse Depends:
  smeg,python-xdg 0.14
  gdesklets-data,python-xdg
  ubuntu-desktop,python-xdg
  kubuntu-desktop,python-xdg
  gnome-app-install,python-xdg 0.8
Dependencies:
0.14-0ubuntu1~5.04ubp1 - python (3 2.5) python (2 2.4)
0.9-1 - python (3 2.5) python (2 2.4)
Provides:
0.14-0ubuntu1~5.04ubp1 -
0.9-1 -
Reverse Provides:

``` 
i.e. it provides both 0.14 AND 0.9-1

I'm guessing that to install smeg you'll have to force it through with:

```

# apt-get --force-yes install smeg

``` 
to push it on to the system.  However, it could break the package.  Post a bug to bugzilla and see what happens?


Sorry this bit is wrong - you might have to force an upgrade with:

```

apt-get -t hoary-backports install python-xdg

```

-- 
Alex.

---

### Post by sd_ap on 2005-10-07
thanks for the reply!

im going to hold off on this as my system is running quite happy sans smeg.  I can wait for the update to breezy... :)

Cheers!

---

