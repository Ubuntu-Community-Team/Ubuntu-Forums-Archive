---
title: "Software updater not working and hanging 19.10"
date: 2020-01-19
forum: General Help
---

### Post by ukfliers on 2020-01-19
I am getting failure to load repository, check internet connection. Pinged and is working fine.Went into settings of Software Updater and now it is hung with the message No software updates are available. This started happening recently.The updater will not quit without me restarting the machine.

---

### Post by ukfliers on 2020-01-19
Also - just opened Ubuntu Software and received this message at top center. "Unable to download updates: failed to refresh cache: E: The repository 'http://ppa.launchpad.net/nemh/systgemback/ubuntu exenial Release' does not have a Release file.

---

### Post by howefield on 2020-01-19
Looks like you have added a PPA which doesn't work with 19.10, in fact seems that this PPA was last updated for Ubuntu 16.10.

If you don't mind using the terminal, please post the output of the following command..

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by coffeecat on 2020-01-19
Forum Feedback and Help is not for general support enquiries.

*Thread moved to **General Help**.*

---

### Post by ukfliers on 2020-01-20
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) eoan main restricted
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) eoan-updates main restricted
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) eoan universe
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) eoan-updates universe
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) eoan multiverse
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) eoan-updates multiverse
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) eoan-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) eoan partner
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security multiverse
/etc/apt/sources.list:deb [http://ppa.launchpad.net/nemh/systemback/ubuntu](http://ppa.launchpad.net/nemh/systemback/ubuntu) exenial main
/etc/apt/sources.list:deb-src [http://ppa.launchpad.net/nemh/systemback/ubuntu](http://ppa.launchpad.net/nemh/systemback/ubuntu) exenial main
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/nordvpn.list:deb [https://repo.nordvpn.com/deb/nordvpn/debian](https://repo.nordvpn.com/deb/nordvpn/debian) stable main
/etc/apt/sources.list.d/nordvpn.list.save:deb [https://repo.nordvpn.com/deb/nordvpn/debian](https://repo.nordvpn.com/deb/nordvpn/debian) stable main

---

### Post by CelticWarrior on 2020-01-20
You need to remove this PPA: [http://ppa.launchpad.net/nemh/systemback/ubuntu](http://ppa.launchpad.net/nemh/systemback/ubuntu) (preferred solution)

-or- 

keep it but correct the distro name: There's no "exenial", it's "**xenial**" and assume the risks of having software not meant for your release.

---

### Post by ukfliers on 2020-01-23
Thank you Celtic Warrior and all those who gave me input. This is all new to me but deleting the ppa line out of my sources.list file as fixed the issues.

---

