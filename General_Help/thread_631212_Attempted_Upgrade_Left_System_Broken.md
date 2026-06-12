---
title: "Attempted Upgrade Left System Broken"
date: 2007-12-04
forum: General Help
---

### Post by abresch on 2007-12-04
I recently decided to go ahead and upgrade to 7.10 from Kubuntu 7.04. I'd run the auto-update thing and everything worked, and it said there was a new version available, and since I had free time ahead, I clicked accept where I'd clicked cancel several times before.

The initial attempt to install choked during the 'Installing the upgrades' portion of the install, giving the error message "subprocess post-installation script killed by signal (Segmentation fault), core dumped" when it tried to install "debconf".

Following this error, the subsequent several items gave the error "dependency problems - leaving unconfigured", then it went back to the error debconf gave again.

After that, it seemed to think it was working, but it was just hanging indefinitely on "Configuring zlib1g". I say indefinitely because I went to work and came back 9 hours later and it hadn't progressed at all, at which point I closed the upgrade and tried to do something manually with Adept Manager.

Now, any attempt to run any updates gives the following errors:

```
*** stack smashing detected ***: /usr/bin/perl terminated
Segmentation fault (core dumped)
Setting up debconf (1.5.14ubuntu1) ...
*** stack smashing detected ***: /usr/bin/perl terminated
dpkg: error processing debconf (--configure):
 subprocess post-installation script killed by signal (Segmentation fault), core dumped
dpkg: dependency problems prevent configuration of libpam0g:
 libpam0g depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing libpam0g (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpam-modules:
 libpam-modules depends on libpam0g (>= 0.99.7.1); however:
  Package libpam0g is not configured yet.
dpkg: error processing libpam-modules (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of login:
 login depends on libpam-modules (>= 0.72-5); however:
  Package libpam-modules is not configured yet.
 login depends on libpam0g (>= 0.76); however:
  Package libpam0g is not configured yet.
dpkg: error processing login (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 debconf
 libpam0g
 libpam-modules
 login
```

The auto-update feature now always says there are 692 updated packages available. If I run that, it fails as all other installation attempts do now, then says there's a version upgrade available. If I attempt that, it fails identically to the original upgrade attempt.

I have not restarted the computer so a lot of my system is still functional, but I suspect if I do reboot, things will really fall apart.

So, any suggestions to fix this?

---

