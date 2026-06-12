---
title: "Can't install xorg-dev -- libxss-dev dependency problem"
date: 2007-03-18
forum: General Help
---

### Post by Jorenko on 2007-03-18
I'm trying to install xorg-dev, but it looks like there's a problem processing one of its dependencies (libxss-dev).

The important parts have been bolded/italicized.

```

**jorenko@jorenko:~$ sudo apt-get install xorg-dev**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
**  xorg-dev: Depends: libxss-dev but it is not going to be installed**
E: Broken packages
**jorenko@jorenko:~$ sudo apt-get install libxss-dev**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
**  libxss-dev: Depends: libxss1 (= 1:1.0.1-4ubuntu1) but *1:1.1-0ubuntu1* is to be installed**
E: Broken packages
**jorenko@jorenko:~$ sudo apt-get install libxss1**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**libxss1 is already the newest version.**
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

---

### Post by yabbadabbadont on 2007-03-18
If you have any 3rd party repositories enabled, disable them, run "sudo apt-get update", then try installing it again.  If you only have ubuntu repos, which ones? (dapper, edgy, fiesty)

---

### Post by Jorenko on 2007-03-21
Okay, I removed the wine repos from my sources. Here's what remains.

```

deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted #Added by software-properties

deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe multiverse main restricted #Added by software-properties

deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse #Added by software-properties

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security restricted main universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb http://security.ubuntu.com/ubuntu/ edgy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ edgy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ edgy-updates universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ edgy-proposed universe main multiverse restricted

```

After `apt-get update` I have the same problem, still. Note that the problem seems to be that apt-get can't decide whether refer to the package by its name or its version. (See the italics in my first post)


Edit: I downloaded libsxss-dev from the web and installed it with dpkg manually. I get past that error now, but there are now about 30 more packages that depend on libxss and break in the same way:
```

The following packages have unmet dependencies.
  libxss-dev: Depends: libxss1 (= 1:1.0.1-4ubuntu1) but 1:1.1-0ubuntu1 is to be installed
  xorg-dev: Depends: libdmx-dev but it is not going to be installed
            Depends: libfontenc-dev but it is not going to be installed
            Depends: libfs-dev but it is not going to be installed
            Depends: libxaw7-dev but it is not going to be installed
            Depends: libxcomposite-dev but it is not going to be installed
            Depends: libxdamage-dev but it is not going to be installed
            Depends: libxevie-dev but it is not going to be installed
            Depends: libxfont-dev but it is not going to be installed
            Depends: libxkbfile-dev but it is not going to be installed
            Depends: libxkbui-dev but it is not going to be installed
            Depends: libxmuu-dev but it is not going to be installed
            Depends: libxpm-dev but it is not going to be installed
            Depends: libxres-dev but it is not going to be installed
            Depends: libxtrap-dev but it is not going to be installed
            Depends: libxtst-dev but it is not going to be installed
            Depends: libxvmc-dev but it is not going to be installed
            Depends: libxxf86misc-dev but it is not going to be installed
            Depends: x11proto-bigreqs-dev but it is not going to be installed
            Depends: x11proto-composite-dev but it is not going to be installed
            Depends: x11proto-damage-dev but it is not going to be installed
            Depends: x11proto-dmx-dev but it is not going to be installed
            Depends: x11proto-evie-dev but it is not going to be installed
            Depends: x11proto-fontcache-dev but it is not going to be installed
            Depends: x11proto-fonts-dev but it is not going to be installed
            Depends: x11proto-gl-dev but it is not going to be installed
            Depends: x11proto-record-dev but it is not going to be installed
            Depends: x11proto-resource-dev but it is not going to be installed
            Depends: x11proto-trap-dev but it is not going to be installed
            Depends: x11proto-xcmisc-dev but it is not going to be installed
            Depends: x11proto-xf86bigfont-dev but it is not going to be installed
            Depends: x11proto-xf86dri-dev but it is not going to be installed
            Depends: x11proto-xf86misc-dev but it is not going to be installed
            Depends: xserver-xorg-dev but it is not going to be installed

```

---

### Post by specvwillis on 2007-03-28
I had the same problem,  I think I picked up a different version of libxss1 from another repo.  I fixed it by going [here]("http://packages.ubuntu.com/edgy/libs/libxss1") and forcing the install of that version.  Hope this helps

---

