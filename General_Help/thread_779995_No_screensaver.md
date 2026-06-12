---
title: "No screensaver"
date: 2008-05-03
forum: General Help
---

### Post by posterpaint on 2008-05-03
I have Kubuntu 4 with no screensavers on the live cd version. Will install load them? And why has ubuntu released K4.0 with other distros waiting a week or more? How did ubuntu get the nvidia drivers for K4.0, fedora and suse say they aren't available? Is K4.0 full of bugs or is there a giant download after the install?
Thanks

---

### Post by Zorael on 2008-05-03
KDE4, much like FF3, is likely to become huge and stable in a few months. But at this point, I don't recommend using KDE4 (at least; I'm sticking to FF2 as well, but that's me).

Consider it a work in progress; it'll likely be a better experience once KDE4.1 hits, of which they've released an alpha recently.

I'd recommend you stick to KDE3 for the time being.

If you've already installed from the Kubuntu KDE4 remix live cd, do this to migrate to the normal KDE3 distro. You may want to do this in recovery mode, but it shouldn't be necessary.
```
$ sudo aptitude install kubuntu-desktop kubuntu-kde4-desktop_  kde4_ kde4-core_ kde4-devel_
$ sudo dpkg-reconfigure kdm
```

---

