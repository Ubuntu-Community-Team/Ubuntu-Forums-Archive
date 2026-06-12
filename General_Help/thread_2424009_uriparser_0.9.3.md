---
title: "uriparser 0.9.3"
date: 2019-08-01
forum: General Help
---

### Post by jamesread5737 on 2019-08-01
I did a sudo apt-get install liburiparser-dev and got the following output:

liburiparser-dev is already the newest version (0.8.4-1).

I really need to be up to date and use version 0.9.3 Is it possible to ask the package maintainers to update to the latest version?

---

### Post by TheFu on 2019-08-01
Not liburiparser specific ....

If the Canonical package isn't new enough for your needs, then you have these possible workaround, in order of preference:
* use a PPA from a respected team, preferably the original project team.
* use a .deb file that is compatible with your release.  Beware that doing this is likely to break the package management dependencies in 3-6 months, so keep a record of any packages installed this way, so you will need to un-install the .deb files, get your system updated, then seek out a fresh version of the .deb file to install.  You are responsible for all updates, security fixes, etc. Lots of manual work, forever.
* use the source code for the version you want, compile it, install it, and setup the project dependencies to use it instead of the default version already installed.  If you go this way, you are responsible for all updates, security fixes, etc. Lots of manual work, forever.

You could open a bug with Canonical to see if someone there will update the package.
You could become the package maintainer yourself and offer it to the Debian project and Canonical. You'll need to have a PPA for some time.

I see that Debian has a 0.9.3 version in their testing release and 0.8.4 are in the old stable Debian version. 

C source code appears to be here: [https://uriparser.github.io/](https://uriparser.github.io/)
I didn't find a PPA.

---

### Post by norobro on 2019-08-01
If you are running 18.04 you can download the packges.   
liburiparser1: [https://packages.ubuntu.com/eoan/liburiparser1](https://packages.ubuntu.com/eoan/liburiparser1)
liburiparser-dev: [https://packages.ubuntu.com/eoan/liburiparser-dev](https://packages.ubuntu.com/eoan/liburiparser-dev)

Then install with dpkg -i.  The only dependency is libc6 >= 2.26 which means bionic or later.

The website says there are no dependencies so if you are running xenial you can download it and compile it yourself. [https://uriparser.github.io/](https://uriparser.github.io/)

EDIT: Hovered over the enter key too long

---

