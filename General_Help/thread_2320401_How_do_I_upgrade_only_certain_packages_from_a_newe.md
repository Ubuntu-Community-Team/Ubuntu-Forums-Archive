---
title: "How do I upgrade only certain packages from a newer distro?"
date: 2016-04-13
forum: General Help
---

### Post by hondaman on 2016-04-13
I need to update to the libvirt version from Xenial Xerus.  I am running trusty tahr.

I don't want to do a dist-upgrade.  I only want to upgrade libvirt.

---

### Post by Bucky Ball on 2016-04-13
A dist-upgrade won't upgrade the OS to a newer version. It only upgrades the software and current OS you have installed.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Something to keep in mind I guess is that if you upgrade one thing it may ask you to drag in dependencies which will replace other dependencies and you may end up with new and old mixing and breakage. But who knows. Let us know what happens.

---

### Post by QDR06VV9 on 2016-04-13
First off "dist-upgrade" dose not take you to a newer os just updates completly all software for **Trusty Only**..
unless I miss understood you.
This link should provide what you are after... if you have all **Deps** needed.
Link to libvirt: [http://www.ubuntuupdates.org/package/core/xenial/main/base/libvirt-bin](http://www.ubuntuupdates.org/package/core/xenial/main/base/libvirt-bin)
Kind Regards
Ninja'd by Bucky

---

### Post by grahammechanical on 2016-04-13
If the version of libvirt that you want is not in the trusty repositories then you have to download it from some where. If you add a xenial repository in order to get the package be careful that other trusty packages do not get upgraded as well.

[https://libvirt.org/downloads.html](https://libvirt.org/downloads.html)

Regards

---

### Post by hondaman on 2016-04-13
Yes, that version of libvirt is what I need.

Is there an easy way to install it and everything it needs?

---

### Post by QDR06VV9 on 2016-04-13
Which Version? There are two links.

---

### Post by montag dp on 2016-04-13
Just so you know, it's dangerous upgrading individual packages from a different repo, especially if it is a system library. It's quite possible that you will find that something else on your system depends on the old version of libvirt, and replacing it by itself will cause those things to stop working. Or, upgrading libvirt may cause a lot of other packages to be upgraded too. There's a reason it takes a lot of work for distros to put together a release, and that is because each package has to be compiled in a consistent environment with a specific set of system libraries in place. Replacing one of those libraries can mess things up.

That aside, the process for doing it probably involves adding the Xenial repos to your sources.list file, but I can't really tell you how to do that without causing conflicts. Maybe someone else can provide info.

---

### Post by mc4man on 2016-04-13
> **hondaman said:**
> Yes, that version of libvirt is what I need.

Is there an easy way to install it and everything it needs?
Not even close. It depends on package versions not in 14.04 that depend on other package versions not in 14.04. So much so that it's not worth detailing. You'll need to find another way

---

### Post by nothingspecial on 2016-04-13
If you explain why you need that version, what you are trying to do, and what you have already tried there may be another solution.

---

### Post by grahammechanical on 2016-04-13
I have only once downloaded software from a Git repository & the software developer provided a readme file to explain what needed to to be done to compile the software into an application. Those instruction are not exactly suitable for you. Except this. To download software from Git we install git

```
sudo apt-get install git
```

Then we clone the software. In your case you do this

```
git clone git://libvirt.org/libvirt.git
```

That downloads the software. What you do next I have no idea. You may get an idea from this

[https://libvirt.org/compiling.html](https://libvirt.org/compiling.html)

Regards

---

