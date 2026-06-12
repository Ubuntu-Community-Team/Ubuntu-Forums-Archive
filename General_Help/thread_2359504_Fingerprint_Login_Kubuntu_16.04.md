---
title: "Fingerprint Login Kubuntu 16.04"
date: 2017-04-24
forum: General Help
---

### Post by norcal618 on 2017-04-24
Hello, I've been trying to get fingerprint authentication working on Kubuntu 16.04 without much luck. I've tried a program called fingerprint gui. I was able to get that to work with authenticating root in the terminal, but was never able to log in through sddm. I read that fingerprint gui works with gdm, so I installed that, followed directions from the fingerprint gui documentation for setting it up with gdm, and I could not get it to work. I've come across some information about another utility called fprint that may work, but I can't find much documentation for it, at least not for Kubuntu. Has anyone here had any luck with enabling fingerprint login with Kubuntu 16.04? If so I would greatly appreciate a nudge in the correct direction. Thank you.

---

### Post by #&amp;thj^% on 2017-04-24
I'm sure you checked that the device is supported by checking here:[https://launchpad.net/~fingerprint/+archive/ubuntu/fingerprint-gui](https://launchpad.net/~fingerprint/+archive/ubuntu/fingerprint-gui)

And these are all installed:
```

libbsapi policykit-1-fingerprint-gui fingerprint-gui
```
For KDE
> Uninstallation
===========
GNOME users: The package policykit-1-fingerprint-gui replaces  GNOME's standard PolicyKit daemon (contained in package  policykit-1-gnome). However, when you decide to uninstall Fingerprint  GUI (and hence remove policykit-1-fingerprint-gui),  policykit-1-gnome will not get automatically installed back, hence there  won't be any PolicyKit daemon in the system, and APT will try to remove  all the packages that depend on it. Therefore, if you want to remove  Fingerprint GUI, make sure you install policykit-1-gnome back first.
   sudo apt-get install policykit-1-gnome
   sudo apt-get remove fingerprint-gui
 KDE SC users: The above instructions for GNOME users apply to you as  well, just replace &#8220;policykit-1-gnome&#8221; by &#8220;polkit-kde-1&#8221; throughout the  text.
 Note for KDE SC users
==================
Please note that Fingerprint GUI doesn't work with kdm and kscreensaver because of a bug in these applications (see [https://bugs.kde.org/show_bug.cgi?id=105631](https://bugs.kde.org/show_bug.cgi?id=105631)).


I'm not sure how secure this method is though (Finger Print Login and not the PPA)...just my 2 cents worth here.
> **Note: **Security warning: Everyone who has access to  both, your computer and the external media, can decrypt the  password-file! Never leave the computer and the media unattended at the  same place! Connect this media only while logon and don't use it if  other persons have root-access to your computer.

---

### Post by norcal618 on 2017-04-25
> **1fallen said:**
> I'm sure you checked that the device is supported by checking here:[https://launchpad.net/~fingerprint/+archive/ubuntu/fingerprint-gui](https://launchpad.net/~fingerprint/+archive/ubuntu/fingerprint-gui)

And these are all installed:
```

libbsapi policykit-1-fingerprint-gui fingerprint-gui
```
For KDE

I'm not sure how secure this method is though (Finger Print Login and not the PPA)...just my 2 cents worth here.

Yea, I came across this stuff. I had libbsapi ... and fingerprint gui installed. I ended up removing both of them, and going back to the original configuration for now because I wasn't having any luck with fingerprint gui.

---

