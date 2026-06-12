---
title: "Can't install or uninstall anything via apt-get"
date: 2007-10-19
forum: General Help
---

### Post by Mateo on 2007-10-19
After I installed gutsy this starting happening.  As an example, I tried uninstalling Rhythmbox and it says this:

```
matthew@matthew-laptop:~$ sudo apt-get remove rhythmbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  feisty-wallpapers libstlport5.1 libgpod1 libslab0 texlive-metapost
  feisty-session-splashes libgs-esp8
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  rhythmbox
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0B of archives.
After unpacking 11.5MB disk space will be freed.
Do you want to continue [Y/n]? y
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 util-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)
matthew@matthew-laptop:~$ 

```

so it looks like there is a problem with tzdata, so i tried reinstalling this.  but that doesn't work.  says this:

```
matthew@matthew-laptop:~$ sudo apt-get install tzdata
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tzdata is already the newest version.
The following packages were automatically installed and are no longer required:
  feisty-wallpapers libstlport5.1 libgpod1 libslab0 texlive-metapost
  feisty-session-splashes libgs-esp8
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of locales:
 locales depends on tzdata; however:
  Package tzdata is not configured yet.
dpkg: error processing locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en-base:
 language-pack-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en-base:
 language-pack-gnome-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of util-linux-locales:
 util-linux-locales depends on util-linux (>= 2.13-0); however:
  Package util-linux is not configured yet.
 util-linux-locales depends on util-linux (<< 2.13.0-0); however:
  Package util-linux is not configured yet.
dpkg: error processing util-linux-locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on locales; however:
  Package locales is not configured yet.
 ubuntu-minimal depends on tzdata; however:
  Package tzdata is not configured yet.
 ubuntu-minimal depends on util-linux; however:
  Package util-linux is not configured yet.
 ubuntu-minimal depends on util-linux-locales; however:
  Package util-linux-locales is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en:
 language-pack-en depends on language-pack-en-base; however:
  Package language-pack-en-base is not configured yet.
dpkg: error processing language-pack-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en:
 language-pack-gnome-en depends on language-pack-gnome-en-base; however:
  Package language-pack-gnome-en-base is not configured yet.
dpkg: error processing language-pack-gnome-en (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 util-linux
 locales
 language-pack-en-base
 language-pack-gnome-en-base
 util-linux-locales
 ubuntu-minimal
 language-pack-en
 language-pack-gnome-en
E: Sub-process /usr/bin/dpkg returned an error code (1)
matthew@matthew-laptop:~$ 

```

So now I don't know what to do.  what do i do?!

---

### Post by por100pre1 on 2007-10-19
That's a bug, read [this]("https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/151449"). Try [this]("https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/151449/comments/2") to fix it.

EDIT: [Read this other bug]("https://bugs.launchpad.net/ubuntu/gutsy/+source/tzdata/+bug/116193"). It seems to be an issue with the time zone.

---

