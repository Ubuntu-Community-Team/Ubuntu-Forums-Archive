---
title: "apt-get Segmentation fault (core dumped)"
date: 2007-09-28
forum: General Help
---

### Post by abhaysahai on 2007-09-28
I am using Linux Mint Celena, which uses Fiesty repositories. 
Mint is almost Fiesty, with some modifications, so please help me with this. 

I did an aptitude update ; aptitude upgrade and now have a broken/unconfigured openoffice.org-common package. 

I have tried many ways including aptitude install -f, dpkg --configure -a, removing openoffice and the re-installing. But no go. 

Please help me with configuring openoffice. 
Here is the output of dpkg --configure -a
```

dpkg --configure -a
Setting up openoffice.org-common (2.2.0-1ubuntu4) ...
Updating OpenOffice.org's dictionary list... done.
Segmentation fault (core dumped)
dpkg: error processing openoffice.org-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-support-en:
 language-support-en depends on openoffice.org-l10n-en-us; however:
  Package openoffice.org-l10n-en-us is not installed.
  Package openoffice.org-common which provides openoffice.org-l10n-en-us is not configured yet.
dpkg: error processing language-support-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-java-common; however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-l10n-en-za:
 openoffice.org-l10n-en-za depends on openoffice.org-common (>= 2.2.0) | language-support-en; however:
  Package openoffice.org-common is not configured yet.
  Package language-support-en is not configured yet.
 openoffice.org-l10n-en-za depends on openoffice.org-common (<< 2.3) | language-support-en; however:
  Package openoffice.org-common is not configured yet.
  Package language-support-en is not configured yet.
dpkg: error processing openoffice.org-l10n-en-za (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-mobiledev:
 openoffice.org-filter-mobiledev depends on openoffice.org-java-common (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-filter-mobiledev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-l10n-en-gb:
 openoffice.org-l10n-en-gb depends on openoffice.org-common (>= 2.2.0) | language-support-en; however:
  Package openoffice.org-common is not configured yet.
  Package language-support-en is not configured yet.
 openoffice.org-l10n-en-gb depends on openoffice.org-common (<< 2.3) | language-support-en; however:
  Package openoffice.org-common is not configured yet.
  Package language-support-en is not configured yet.
dpkg: error processing openoffice.org-l10n-en-gb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
 openoffice.org depends on openoffice.org-filter-mobiledev; however:
  Package openoffice.org-filter-mobiledev is not configured yet.
 openoffice.org depends on openoffice.org-java-common; however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-thesaurus-en-us:
 openoffice.org-thesaurus-en-us depends on openoffice.org-common (>= 2.0) | language-support-en; however:
  Package openoffice.org-common is not configured yet.
  Package language-support-en is not configured yet.
dpkg: error processing openoffice.org-thesaurus-en-us (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org-common
 openoffice.org-java-common
 language-support-en
 openoffice.org-base
 openoffice.org-l10n-en-za
 openoffice.org-filter-mobiledev
 openoffice.org-l10n-en-gb
 openoffice.org
 openoffice.org-thesaurus-en-us 
```

---

### Post by tbroderick on 2007-09-28
You used sudo before aptitude install -f or, dpkg --configure -a, right?

---

### Post by abhaysahai on 2007-09-29
No I did not. 
However, I have used "sudo -s "  to have root privileges. 
Moreover, I I do not have root access,  aptitude install -f will complain. 
Am I right ?

---

### Post by tbroderick on 2007-09-29
I would try sudo dpkg --configure -a and see if it's any differnet.

---

### Post by Poene on 2007-10-07
I have this problem too. I used all of the following commands, but I keep getting the segmentation faults. 

```
 peter@peter-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Segmentation fault (core dumped)
peter@peter-desktop:~$ sudo dpkg --configure -a
Setting up ttf-opensymbol (2.2.0-1ubuntu5) ...
Updating fontconfig cache...
/bin/sh: Can't open fc-cache
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 2.2.0) | openoffice.org-core-experimental (>> 2.2.0); however:
  Package openoffice.org-core is not configured yet.
  Package openoffice.org-core-experimental is not installed.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org depends on openoffice.org-writer; however:
  Package openoffice.org-writer is not configured yet.
 openoffice.org depends on openoffice.org-calc; however:
  Package openoffice.org-calc is not configured yet.
 openoffice.org depends on openoffice.org-draw; however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-base depends on openoffice.org-java-common; however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-mobiledev:
 openoffice.org-filter-mobiledev depends on openoffice.org-java-common (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-filter-mobiledev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-draw
 openoffice.org-gtk
 openoffice.org-calc
 openoffice.org-common
 openoffice.org-writer
 python-uno
 openoffice.org
 openoffice.org-style-human
 openoffice.org-gnome
 openoffice.org-java-common
 openoffice.org-impress
 openoffice.org-base
 openoffice.org-math
 openoffice.org-filter-mobiledev
peter@peter-desktop:~$ 

```

My system broke after I tried to update OpenOffice through the update manager.

---

### Post by @vijay@ on 2007-10-21
im having exactly the same problem as above tried every thing but couldn't fix it

---

### Post by cmittle on 2007-11-14
I am having segmentation fault...error exit status 139 problems as well.  I have tried all of the above mentioned commands as well.  I started a [thread]("http://ubuntuforums.org/showthread.php?t=608879&highlight=error+exit+139") a little bit ago about these problems, but nobody seems to have an answer for these.  Could someone at least decode what the output is telling me so I can attempt to look around and fix it myself?

---

### Post by zebralinux on 2008-04-20
i did this to solve it:

§ cd /var/cache/apt

§ rm pkgcache.bin  srcpkgcache.bin

this files got corrupted apperently.
They will get auto gererated by apt so dont worry

---

