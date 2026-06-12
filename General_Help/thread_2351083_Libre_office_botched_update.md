---
title: "Libre office botched update"
date: 2017-01-30
forum: General Help
---

### Post by UncleMonty on 2017-01-30
I'm not certain what the problem is, all I know is libre office seems to look like KDE, the toolbar writing is too small to read, and whenever I try to save files I get offered a path that includes servers. I attempted to upgrade to the latest version of libre office but seem to have botched it. How can I identify what libreoffice version I've got? I've tried purging via terminal, and reinstalling via snypatic but just end up in the same situation. 

Information I can give:
```

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial
```

---

### Post by vasa1 on 2017-01-30
```
apt-cache policy libreoffice
``` should give you the version. You can paste the entire output here within code tags.

Another option with simpler output is this:```
apt list --installed | grep libreoffice

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

libreoffice-base-core/now 1:5.2.4~rc2-0ubuntu1~xenial2 amd64 [installed,local]
libreoffice-calc/now 1:5.2.4~rc2-0ubuntu1~xenial2 amd64 [installed,local]
libreoffice-common/now 1:5.2.4~rc2-0ubuntu1~xenial2 all [installed,local]
libreoffice-core/now 1:5.2.4~rc2-0ubuntu1~xenial2 amd64 [installed,local]
libreoffice-gtk2/now 1:5.2.4~rc2-0ubuntu1~xenial2 amd64 [installed,local]
libreoffice-help-en-us/now 1:5.2.4~rc2-0ubuntu1~xenial2 all [installed,local]
libreoffice-math/now 1:5.2.4~rc2-0ubuntu1~xenial2 amd64 [installed,local]
libreoffice-style-elementary/now 1:5.2.4~rc2-0ubuntu1~xenial2 all [installed,local]
libreoffice-style-galaxy/now 1:5.2.4~rc2-0ubuntu1~xenial2 all [installed,local]
libreoffice-style-tango/now 1:5.2.4~rc2-0ubuntu1~xenial2 all [installed,local]
libreoffice-writer/now 1:5.2.4~rc2-0ubuntu1~xenial2 amd64 [installed,local]

```I got mine via a ppa. So your version may be different.

---

### Post by DuckHook on 2017-01-30
It seems to me like your problem is likely more to do with some configuration file than your version.

Some apps like Libreoffice do not completely go back to a virgin state even if you invoke the -purge flag. This is understandable; where would it stop? Does it purge that template that you may have spent hours customizing? Since this app is so intimately tied in with your data, it subscribes to the principle that discretion is the better part of valour. Hence, a corrupted config file may still hang around messing up every re-install no matter how many times you purge.

I've found that the best strategy when dealing with such deeply embedded default apps is to fire up a LiveUSB of your exact flavour and version and do a *diff* comparison between the config file(s) on your HDD and the one(s) on the LiveUSB.

Here's a nice short tutorial on *diff* usage: [http://linoxide.com/linux-command/linux-diff-command-examples/](http://linoxide.com/linux-command/linux-diff-command-examples/)

There are many graphical equivalents, all easily installed from the repos: meld, xxdiff, diffuse, etc.

---

### Post by DuckHook on 2017-01-30
It should also be noted that libre*office* is a metapackage consisting of the packages: writer, calc, impress, etc. Purging the metapackage won't achieve anything. The underlying real packages are the ones that need to be purged.

But, as mentioned, I think it's probably best to compare config files first before purging anything.

---

### Post by vasa1 on 2017-01-30
> **DuckHook said:**
> It seems to me like your problem is likely more to do with some configuration file than your version.

Some apps like Libreoffice do not completely go back to a virgin state even if you invoke the -purge flag. This is understandable; where would it stop? Does it purge that template that you may have spent hours customizing? Since this app is so intimately tied in with your data, it subscribes to the principle that discretion is the better part of valour. Hence, a corrupted config file may still hang around messing up every re-install no matter how many times you purge.
...
Renaming ```
~/.config/libreoffice/4/user
```to something else after making sure no process of LibreOffice is running will give the user a pristine config.

Re. purging, here's partial output from```
apt-get purge -s libreoffice*
```

```
...
The following packages were automatically installed and are no longer required:
  fonts-opensymbol fonts-stix libboost-date-time1.58.0 libboost-iostreams1.58.0
  libclucene-contribs1v5 libclucene-core1v5 libexttextcat-2.0-0 libexttextcat-data
  libglew1.13 liblangtag-common liblangtag1 libmythes-1.2-0 uno-libs3 ure
Use 'apt autoremove' to remove them.
The following packages will be REMOVED:
  libreoffice-base-core* libreoffice-calc* libreoffice-common* libreoffice-core*
  libreoffice-gtk2* libreoffice-help-en-us* libreoffice-math*
  libreoffice-style-elementary* libreoffice-style-galaxy* libreoffice-style-tango*
  libreoffice-writer* python3-uno*
0 upgraded, 0 newly installed, 12 to remove and 0 not upgraded.
Purg libreoffice-help-en-us [1:5.2.4~rc2-0ubuntu1~xenial2]
Purg libreoffice-writer [1:5.2.4~rc2-0ubuntu1~xenial2]
Purg libreoffice-calc [1:5.2.4~rc2-0ubuntu1~xenial2]
Purg libreoffice-base-core [1:5.2.4~rc2-0ubuntu1~xenial2]
Purg python3-uno [1:5.2.4~rc2-0ubuntu1~xenial2]
Purg libreoffice-gtk2 [1:5.2.4~rc2-0ubuntu1~xenial2]
Purg libreoffice-core [1:5.2.4~rc2-0ubuntu1~xenial2] [libreoffice-math:amd64 ]
Purg libreoffice-style-tango [1:5.2.4~rc2-0ubuntu1~xenial2] [libreoffice-math:amd64 ]
Purg libreoffice-common [1:5.2.4~rc2-0ubuntu1~xenial2] [libreoffice-math:amd64 libreoffice-style-galaxy:amd64 libreoffice-style-elementary:amd64 ]
Purg libreoffice-math [1:5.2.4~rc2-0ubuntu1~xenial2] [libreoffice-style-galaxy:amd64 libreoffice-style-elementary:amd64 ]
Purg libreoffice-style-elementary [1:5.2.4~rc2-0ubuntu1~xenial2] [libreoffice-style-galaxy:amd64 ]
Purg libreoffice-style-galaxy [1:5.2.4~rc2-0ubuntu1~xenial2]

```

---

### Post by DuckHook on 2017-01-30
> **vasa1 said:**
> Renaming ```
~/.config/libreoffice/4/user
```to something else after making sure no process of LibreOffice is running will give the user a pristine config.…a clever strategy.
> Re. purging, here's partial output from```
apt-get purge -s libreoffice*
```…Most users will not know enough to append the wildcard (*).

@OP What vasa1 is referring to are the packages that actually make up libreoffice. The relevant parts from:```
apt show libreoffice
``````
Description: office productivity suite (metapackage)
 LibreOffice is a full-featured office productivity suite that provides
 a near drop-in replacement for Microsoft(R) Office.
 .
 This metapackage installs all components of libreoffice:
 * libreoffice-writer: Word processor
 * libreoffice-calc: Spreadsheet
 * libreoffice-impress: Presentation
 * libreoffice-draw: Drawing
 * libreoffice-base: Database
 * libreoffice-math: Equation editor
```…hence the use of the wildcard.

---

### Post by vasa1 on 2017-01-31
> **DuckHook said:**
> ...
I've found that the best strategy when dealing with such deeply embedded default apps is to fire up a LiveUSB of your exact flavour and version and do a *diff* comparison between the config file(s) on your HDD and the one(s) on the LiveUSB.
...
Some of the user's configs are in ```
~/.config/libreoffice/4/user/registrymodifications.xcu
```and that's a really nasty file to *diff*. The way it's formatted seems to discourage casual poking around. It's one long line ... :(

I posted about that file [before]("https://ubuntuforums.org/showthread.php?t=2283711&highlight=libreoffice") but didn't get any bites. My current file is 258 KiB. Turning off thumbnails and recent docs brought it down from ~1.6 MiB.

BTW, I wonder if OP has any of the following:```
apt search libreoffice | grep integration

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

  office productivity suite -- GNOME integration
  office productivity suite -- GTK+ integration
  office productivity suite -- GTK+ 2 integration
  office productivity suite -- GTK+ 3.0 integration
  office productivity suite -- KDE integration

```

---

### Post by DuckHook on 2017-01-31
Didn't even know about that file. Man, how I hate this "registry" direction that systemd is taking us, but that's a topic for another day.

@OP

Perhaps a further purge is in order after all, but you must use vasa1's version with the wildcard, else you will just be purging a wrapper and not the content. First, though, try his trick with moving the whole directory.

---

