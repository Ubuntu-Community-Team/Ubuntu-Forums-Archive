---
title: "synpatic error message"
date: 2007-01-14
forum: General Help
---

### Post by xGutsAndGloryx on 2007-01-14
E: wpasupplicant: Package is in a very bad inconsistent state - you should

---

### Post by taurus on 2007-01-14
> **xGutsAndGloryx said:**
> E: wpasupplicant: Package is in a very bad inconsistent state - you should

Is that the whole error message?

---

### Post by xGutsAndGloryx on 2007-01-14
yes, thats all synpatic gave.. i believe it said, " something about uninstalling it." it won't let me uninstalling it.

---

### Post by taurus on 2007-01-14
Run it from a terminal to see what's the problem.

Applications -> Accessories -> Terminal
```
sudo aptitude update
(and if there is no error message from the command above, continue with the next command...)
sudo aptitude upgrade
```

---

### Post by xGutsAndGloryx on 2007-01-14
> **taurus said:**
> Run it from a terminal to see what's the problem.

Applications -> Accessories -> Terminal
```
sudo aptitude update
(and if there is no error message from the command above, continue with the next command...)
sudo aptitude upgrade
```


that didn't work

---

### Post by taurus on 2007-01-14
The first command didn't work!  Can you please post the whole error message because it's kind of hard to figure out what's wrong with it when we only have "that didn't work"?

---

### Post by ~LoKe on 2007-01-14
> sudo gedit /var/lib/dpkg/status
Search for "wpa".  It'll show you an entire block of information relating to wpa_supplicant.  It'll look something like this:
> Package: wpasupplicant
Status: install ok installed
Priority: important
Section: net
Installed-Size: 1056
Maintainer: Trevi <trevi55@gmail.com>
Architecture: i386
Version: 0.5.7+3v1ubuntu3
Replaces: wpagui
Provides: wpagui
Depends: libc6 (>= 2.4-1), libdbus-1-3, libgcc1 (>= 1:4.1.1-12), libncurses5 (>= 5.4-5), libqt3-mt (>= 3:3.3.6), libreadline5 (>= 5.1), libssl0.9.8 (>= 0.9.8b-1), libstdc++6 (>= 4.1.1-12), libx11-6, libxext6
Suggests: kwlan
Conflicts: wpagui
Conffiles:
 /etc/default/wpasupplicant edd42614b0f4aed23dba9b17fdefa998
 /etc/wpa_supplicant.conf a3539c641835b2d2b59b399fc01ecba9
Description: Client support for WPA and WPA2 (IEEE 802.11i)
 WPA and WPA2 are methods for securing wireless networks, the former
 using IEEE 802.1X, and the latter using IEEE 802.11i. This software
 provides key negotiation with the WPA Authenticator, and controls
 association with IEEE 802.11i networks.
 This package includes also wpa_gui, a qt front-end for wpa_cli

Erase **the entire block**.  Save and close.
> sudo apt-get upgrade

Enjoy.

---

### Post by xGutsAndGloryx on 2007-01-14
E: /var/cache/apt/archives/wpasupplicant_0.5.7+3v1ubuntu1_i386.deb: subprocess new post-removal script returned error exit status 10



here is more information about the error message


please help me

---

### Post by xGutsAndGloryx on 2007-01-14
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
xgutsandgloryx@xgutsandgloryx:~$

---

### Post by ~LoKe on 2007-01-14
You removed the **entire** block relating to wpa_supplicant, right?  Just that block, I hope?

**EDIT:** I think you removed the wrong thing, or all of it.  Do this:
> sudo cp /var/lib/dpkg/status~ /var/lib/dpkg/status && sudo cp /var/lib/dpkg/status /var/lib/dpkg/status_back && sudo gedit /var/lib/dpkg/status
Remove ONLY the wpa_supplicant section.

---

