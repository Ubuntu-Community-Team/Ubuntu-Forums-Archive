---
title: "How do I install software later than shown in official repositories?"
date: 2015-08-08
forum: General Help
---

### Post by Brent_Santin on 2015-08-08
Hi, I've been using Lubuntu 14.04 Trusty Tahr for over a year and really like it.  I have noticed, however that some of my favourite applications (Inkscape and Kdenlive video editor) now have current release versions that are later than what is offered to me by Lubuntu's software repository (I'm using the built in Lubuntu Software Center and Synaptic Package Manager). I wouldn't mind being able to update both InkScape and Kdenlive, as I  have discovered a few small bugs, stability issues which have been fixed  in later versions, as well as new features that have been added.

For instance, the latest version of Kdenlive offered to me by Lubuntu's built-in software manager(s) is 0.9.5 while the current stable version is actually 15.4.2. The Kdenlive website recommends version 0.9.10 for Ubuntu. These versions are all later than what I am offered by Lubuntu's package manager(s).

I have discovered that in Synaptic Package Manager, when I left click on the choice for Kdenlive, I can select "mark for update", but this is greyed out (no updates avalable).

So I have a few questions:

a) is there any reason why I would not try and install these later software versions?  Does Lubuntu 14.04 NEED the older versions for some reason?
b) why do the latest versions NOT show up in my package managers / repositories?
c) If my package manager will not offer me the lastest stable packages, and it is okay to install them anyway?  If so, how do I go about it?   I'm still learning about Linux. I know I can download DEB files and install them manually.  I can also add repositories that offer the latest version - in fact, that is what the Kdenlive website seems to recommend for Ubuntu users ([https://kdenlive.org/download-ubuntu](https://kdenlive.org/download-ubuntu)):

[INDENT]Versions of Kdenlive in official repositories may be deprecated. You can install the latest stable release using Sunab's alternative repository:
You can check what versions this repository will install from here [URL="https://launchpad.net/%7Esunab/+archive/kdenlive-release"]https://launchpad.net/~sunab/+archive/kdenlive-release
[/URL][/INDENT]
[URL="https://launchpad.net/%7Esunab/+archive/kdenlive-release"] 
[/URL][INDENT]To use the Sunab's alternate repository:

[/INDENT]
[INDENT]type 'Software Sources' in Unity Dash > Other Software ; or  use your favourite System Menu and look for Software Sources > Other  Software ;
[/INDENT]
[INDENT]click add and paste this line in:
[/INDENT]
[INDENT]ppa:sunab/kdenlive-release
[/INDENT]
[INDENT]close software source and click reload.
[/INDENT]

So, I'm not exactly sure what to do, or what is safe to do.  Advice or instructions would be appreciated.  I don't want to bugger up my very nicely working Lubuntu installation. Thanks.

---

### Post by howefield on 2015-08-08
Many of your questions will be answered here..

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

It is generally safe to use PPAs if they are from a trusted party but would suggest you stick to only those who offer Lubuntu 14.04 repositories.

---

### Post by Vladlenin5000 on 2015-08-08
a) The version available in the Ubuntu repositories has been tested and audited. All the others hasn't. Besides this, no other reason.
b) The aforementioned process takes time and only a handful of apps are actually updated after the version freeze (example: Firefox).
c) Any non-official version is riskier than the tested ones, obviously. Installing newer versions should be done preferably with third party PPAs; installing via a random .deb file should be the last of your options. The KDEnlive method you correctly described is the former.

Generally speaking, using PPAs for newer version of some selected software is safe. Although those versions hadn't been tested by the Ubuntu team directly, they usually are prepared by people who test it and make sure it works in the Ubuntu version for which it is set up. Usually there are no problem with that approach but the downside is that you _should_ disable, albeit momentarily, each and any of those third party PPA when you're upgrading from one Ubuntu release to the next. KDEnlive is pretty safe. I know many people that added the recommended PPA and upgrade the KDEnlive version without any issues.

---

### Post by Simon_Tomoko on 2015-08-08
Another way to install a backport is this;

I prefer GIMP 2.6 but 14.04 forces 2.8 so I added these text files in /etc/apt/sources.list.d/

saved as: precise-for-gimp.list 
```
deb http://nl.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted

```

saved as: precise-for-gimp.list.save
```

deb http://nl.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted

```

This way it ONLY effects my GIMP and nothing else.

---

### Post by Brent_Santin on 2015-08-08
Just so I understand: software in the repository are essentially "frozen" at certain tested & known to work versions with each release of the OS?  Except for a handful?  i.e. Firefox, and I believe LibreOffice has updated automatically for me.

Do I need to uninstall the old version of Kdenlive before installing the new version?

...and if the new non-audited version gives me problems on Lubuntu, is it easy to uninstall and roll back to an earlier version?

---

### Post by Vladlenin5000 on 2015-08-08
That's it pretty much... There are also security updates whenever needed and others prompted by kernel updates.
And they must be frozen for the most part. We would have a rolling release otherwise.

---

