---
title: "Why is &quot;libunity-scopes-json-def-desktop&quot; part of non-Unity flavors?"
date: 2013-10-19
forum: General Help
---

### Post by vasa1 on 2013-10-19
I noticed an update for **libunity-scopes-json-def-desktop**. To find out what that is, I ran **apt-cache show libunity-scopes-json-def-desktop** and saw this, in part:
```
[10:44 AM] ~ $ apt-cache show libunity-scopes-json-def-desktop
Package: libunity-scopes-json-def-desktop
Priority: optional
Section: gnome
Installed-Size: 52
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: libunity
Version: 7.1.2+13.10.20131010-0ubuntu2
...
...
Description-en: binding to get places into the launcher - desktop def file
 libunity is a shared library to be able to interact with the launcher
 and add places in Unity environment.
...
 This package contains default scopes definition for the destkop.
...
...
Task: ubuntu-desktop, ubuntu-usb, edubuntu-desktop, edubuntu-usb, **xubuntu-desktop**, **lubuntu-desktop**, ubuntustudio-desktop, ubuntu-gnome-desktop
```
Why does Lubuntu (and probably Xubuntu) carry this package?

---

### Post by vasa1 on 2013-10-19
Also posted here: [http://askubuntu.com/questions/362198/why-is-libunity-scopes-json-def-desktop-part-of-non-unity-flavors-in-13-10](http://askubuntu.com/questions/362198/why-is-libunity-scopes-json-def-desktop-part-of-non-unity-flavors-in-13-10)

---

### Post by oldos2er on 2013-10-20
Found out this was installed on my system too, Ubuntu Server with X and i3-wm. I don't have any of the *buntu-desktop packages installed, and I'm not sure if it was installed as a dependency of another package. I removed it (and libunity9 too) without incident.

---

### Post by vasa1 on 2013-10-20
> **oldos2er said:**
> Found out this was installed on my system too, Ubuntu Server with X and i3-wm. I don't have any of the *buntu-desktop packages installed, and I'm not sure if it was installed as a dependency of another package. I removed it **(and libunity9 too)** without incident.
Because of the part in bold, I search /var/log/apt/history.log for "unity" and found:
```

gir1.2-unity-5.0, GObject introspection data for the Unity library
libunity-protocol-private0, binding to get places into the launcher - private library
libunity-scopes-json-def-desktop, binding to get places into the launcher - desktop def file
libunity9, binding to get places into the launcher - shared library
```
As for removing them, as a **desktop** user, I'll wait on that. For example, there's psensor (which I no longer use): 
**apt-cache showpkg libunity9** has psensor as a reverse depend and
**apt-cache shopkg psensor** has libunity9 listed as a dependency.

I'll check out the others later but my suspicion, based on just one instance, is that the aim of integrating (with Unity) maybe the reason why cross-platform apps list these unity-related packages. But other quite common packages have libunity9 as their dependency.

---

