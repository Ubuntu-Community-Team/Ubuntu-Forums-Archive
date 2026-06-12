---
title: "Unable to install DEBs  since installing 23.10"
date: 2023-10-23
forum: General Help
---

### Post by daj_uk on 2023-10-23
I have just completed a  install of 23.10.  Clean install, not an upgrade.  All appeared to go well but when I try to install apps nothing happens.

In the past, if the app was not in the App Centre, I would download the .DEB then right click on the file and "Open With App Centre".   This used to work in earlier version (22.04).  Now the App Centre loads and I get a spinning orange disk.  I've tried a few downloads, all the same.  I I find an App in the App Centre, it will install as expected.

I've read that there were changes to the App Centre -- is there a different way to load Apps outside the list now?

thanks

---

### Post by LewisTM on 2023-10-23
This has been lamented by others, see OMGUbuntu's [article]("https://www.omgubuntu.co.uk/2023/10/install-deb-ubuntu-23-10-no-app-error").

Basically you have to install Gdebi from the App Center or the command line to be able to install .deb files.

Cheers!

---

### Post by daj_uk on 2023-10-23
Awesome.  Thanks for the response and the link.

Looks lie the new App Centre has taken a step back for the moment.  At least I can not resolve my issue

---

### Post by #&amp;thj^% on 2023-10-23
The terminal works as well, and as far as this gdebi:
```
apt policy gdebi
gdebi:
  Installed: 0.9.5.7+nmu7
  Candidate: 0.9.5.7+nmu7
  Version table:
 *** 0.9.5.7+nmu7 500
        500 http://archive.ubuntu.com/ubuntu mantic/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu mantic/universe i386 Packages
        100 /var/lib/dpkg/status

```
Easy to install:
```
sudo apt install gdebi
```
NOTE: I'm completey void of any snaps here.
If your still having problems show us a ".deb" you can't install.

---

### Post by Frogs Hair on 2023-10-24
Also be sure your package is compatible with 23.10. Some apps are only updated for Ubuntu LTS releases.

---

### Post by ian-weisser on 2023-10-24
Or even easier...

```

sudo apt install /path/to/package_name.deb

```

...but you're not using deb packages the way they are intended to be used (via a distro).
So you won't get updates for it. You won't get security patches for it.
Eventually it will be incompatible with a future release of Ubuntu. That means it will either break without warning...or it will mysteriously block the release-upgrade.

"I can't use Ubuntu Software to install it" is indeed a (temporary) problem. But it's not the biggest problem with that workflow.

---

### Post by iamjiwjr on 2023-10-24
The Zoom client deb will not install on 23.10 due to dependency issues (the snap Zoom client had webcam crashes and virtual desktops didn't work for me). But if you go to ubuntuhandbook.org and search Zoom, there's an article walking you through getting the needed dependencies so install works. Then the Zoom deb client works great.

---

