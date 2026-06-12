---
title: "Sweet Home 3D how to upgrade"
date: 2017-08-04
forum: General Help
---

### Post by gibsonsimswilson on 2017-08-04
Hello

I used the software centre to install Sweet Home 3D and the version is 4.5. On their website they have version 5.4

How do I upgrade?

And just a question... Why is the software centre so far behind on upgrades?

Thanks

Gibby

16.04

---

### Post by texpat on 2017-08-04
Hi Gibby,

to install the latest, go to [http://www.sweethome3d.com/download.jsp](http://www.sweethome3d.com/download.jsp) and download the version you need: 32 or 64 bit. It says how to install on that same page. 

I haven't done so myself, but it looks like its Java so it should be relatively simple (as in: no compiling etc involved), although  you may have to create your own desktop/menu shortcut.

I'm not sure if it is necessary, but I would uninstall the exiting version from the computer before installing the new one. Uninstalling the downloaded software should be as simple as deleting the folder it sits in.

As to why the repos are not so up to date I would surmise that stuff allowed into them has to be tested and considered "stable". That is a lot of work, especially if you do it for free.

---

### Post by Bucky Ball on 2017-08-04
> **texpat said:**
> As to why the repos are not so up to date I would surmise that stuff allowed into them has to be tested and considered "stable". 

+1. Which version of Ubuntu you are using will have something to do with which version of SweetHome you are seeing in the repos also, naturally.

One would presume you are not using 9.10, as your profile suggests!

---

### Post by vocx on 2017-08-04
> **gibsonsimswilson said:**
> Hello

I used the software centre to install Sweet Home 3D and the version is 4.5. On their website they have version 5.4

How do I upgrade?

And just a question... Why is the software centre so far behind on upgrades?

Thanks

Gibby

16.04
The software that is installed by the Software center, or through the "apt-get" terminal commands, comes from the Ubuntu repositories. The repositories contain software packages made by package maintainers who take the source code from the developers and package it in a way that is suitable for Debian and Ubuntu. Once the software is packaged for one version of Ubuntu, say 16.04, it stays at that version, frozen. So, the package is not updated any more during the life of the Ubuntu 16.04 version.

Before a new version of Ubuntu is released, say, 16.10 or 17.04, the package maintainers take a newer version of the software from the developers and again package it. This means that the software in the Ubuntu repositories only changes every six months to coincide with the distribution release. Say, for a package A, in 16.04 it is at version 1.0, then in 16.10 it may be at 2.0, and in 17.04 it may be at 3.0. If you keep using 16.04 you may always have the version that came with it, which is 1.0. If you want the latest version, 3.0, you either have to install it yourself, or move the entire system to 17.04.

Why is this done? To keep stability in the system. Many packages depend on the functionality of others, so Ubuntu guarantees a stable system with fixed versions of the packages in its repositories. It is implied that a power user will be able to get the newest version of a particular software if he or she really needs it. This is not a problem for software that doesn't change much. However, for new programs that are under heavy development this necessarily results in an old version living in the repositories, while the latest version is only available at the original developer's website.

---

### Post by QIII on 2017-08-04
Moved to General Help.

Installation & Upgrades is intended for installation and upgrade of the OS, not software packages.

Cheers.

---

### Post by vocx on 2017-08-04
> **texpat said:**
> ...
As to why the repos are not so up to date I would surmise that stuff allowed into them has to be tested and considered "stable". That is a lot of work, especially if you do it for free.
> **Bucky Ball said:**
> +1. Which version of Ubuntu you are using will have something to do with which version of SweetHome you are seeing in the repos also, naturally...
I don't think this is exactly correct.

Basically, Ubuntu has a "feature freeze" some two months before the launch of the new Ubuntu version. So, it is not that the package is "tested" for stability per se, but rather, the version in the repository is the version that was available when the feature freeze occurred. Of course, Ubuntu tests many components essential to the operating system, like the Kernel and the desktop environment, and makes small improvements to them. But I think for the bulk of the individual packages intended for the common user, there is no testing, they are just frozen versions of the package.

---

### Post by again? on 2017-08-05
You can get 5.4 deb for xenial from [ubuntuupdates.org]("https://www.ubuntuupdates.org/package/getdeb_apps/xenial/apps/getdeb/sweethome3d")
Best method to install deb files is install and use gdebi.

---

