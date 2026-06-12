---
title: "Remove all non default (standard) packages"
date: 2016-09-09
forum: General Help
---

### Post by XCan on 2016-09-09
I have one particular machine which has been running Ubuntu for quite some time, since Ubuntu 10.04. This means that the distribution has been upgrade many times.

Since every new upgrade carries its own default packages I now have quite a lot of non-default packages (where most I do not even use) piling up. It would thus be nice to be able to get rid of these "useless" packages.

However, my problem is that I have not figured out a feasible way to sorts out the packages that are not part of a standard Ubuntu installation, i.e., is there a way to compare the list of packages that are installed by default to a list of all my currently installed packages?

---

### Post by HermanAB on 2016-09-09
Howdy,

You are trying to unscramble eggs.

The best you can do is to edit the menus and remove entries for things you don't want to see and don't actually remove anything, since by uninstalling packages, it is too easy to end up with a non-functional system.

---

### Post by #&amp;thj^% on 2016-09-09
HermanAB is correct in You are trying to unscramble eggs.
But if you really need to... there are manifest list's for each release you could read through and compare..(Lots of time needed to this)
Just an example here For 14.04.5 i368: [http://releases.ubuntu.com/14.04/ubuntu-14.04.5-desktop-i386.manifest](http://releases.ubuntu.com/14.04/ubuntu-14.04.5-desktop-i386.manifest)
Sounds fun don't it?:D

---

### Post by Keith_Helms on 2016-09-10
What difference does it make if it's a "default" package?  If you don't use an application, you can uninstall it.  I wouldn't fiddle with uninstalling libraries and such - that is liable to get you in trouble.  Just concentrate on the things that show up in the menus.   For example, if you don't use the Rhythmbox player, you can uninstall it and it shouldn't matter whether that's the default player for 16.04.  Don't edit photos - get rid of Gimp, and so on.

Although the option to upgrade is provided, there is something to be said for doing a clean install.  Having a 2nd boot partition and doing a fresh install of the latest release in there allows you to continue booting the older release if the new one doesn't work right on your hardware.  Keeping everything in a single partition and doing upgrades whenever an LTS release comes along guarantees that unused stuff will build up over time.

---

### Post by XCan on 2016-09-11
I do have root on a separate partition, although doing clean installs every release or even every LTS makes the whole thing even worse than Windows, and it must be absolute non-sense to design a system that was recommended to be reinstalled once in a while...

The difference it makes if it is a default package is exactly to preventing the removal of essential packages that would require a re-installation. I am aware of the manifest files, and comparing to their contents is not too difficult 'comm' and 'aptitude'. Although, from what I have learned, this is not entirely water proof, as the manifest does not include all the packages (different theories exist here). But it would be far more correct to instead of the manifest package use the contents in, /var/log/installer/initial-status.gz. However, the contents in a system that has been upgraded would obviously be not very useful for the purpose in this thread...

At least a way to list packages that have not been used for a very long time would be nice for a clean-up.

---

### Post by Keith_Helms on 2016-09-11
There is nothing that will tell you how recently a command or application has been used and certainly nothing that would then set a last-used date on the install package for that command or application.

If you want to get rid of "orphan" libraries and such, you can run
```
sudo apt-get autoremove
```

Is there some reason you're worrying about this?  Too many old programs appearing on menus or too much disk space being used?

---

