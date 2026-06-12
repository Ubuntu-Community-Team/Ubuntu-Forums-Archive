---
title: "Questions about versions updated in Software Center and/or Synaptic"
date: 2021-10-17
forum: General Help
---

### Post by jmichaels29 on 2021-10-17
I was just curious about how Ubuntu Software center and/or Synaptic Package Manager works.
 
For example, I recently have Gimp version 2.10.18-1 installed.  I know that there is a more up to date stable version of it in the depositories. 
I assumed that Ubuntu updates would take it upon themselves to update Gimp to a newer stable version, however it hasn't. 
Is the general way this works is that the user needs to remove the current version of software before they can manually install a newer version?  I had previously assumed it would occur during a software update....

Addendum:  Gimp version 2.10.18-1 is also the "latest version" when I open Synaptic Package Manager....  So I guess I'd need to remove this version, then search for Gimp to find the most recent stable version in there too?

---

### Post by grahammechanical on 2021-10-17
This is the way it works. We get a new Ubuntu version every six months in either April or October. Also Every two years the April release is given five years support and is called a Long Term Support (LTS) version. The other versions only get nine months support. Certain applications in LTS versions get upgraded during the support period. LibreOffice and Firefox are two of these applications. Most other applications do not get upgraded and there are two reasons I can think of.

1) The developers of the application have not upgraded their application.
2) The upgraded version has not been code audited to confirm that there is nothing in the code that will do bad things to our installations. New versions of applications are usually put in the repositories of the new releases of Ubuntu and are not upgraded during the support period.

I do not know if the Gimp is one of those applications that get upgraded during the life of an LTS version. I guess that if you are not running an LTS version you will not see a newer version of the Gimp until you upgrade to the next Ubuntu release.

Synaptic Package Manager and Ubuntu Software access the repositories of the version of Ubuntu that we are using at the time. They do not access any software stores of application developers. So, they are unaware of any newer versions until those versions get added to a repository and those will usually be repositories of the next versions of Ubuntu.

Regards

---

### Post by Dennis N on 2021-10-17
>  So I guess I'd need to remove this version, then search for Gimp to find the most recent stable version in there too? 
Ubuntu provides Snap packages with newer versions of many applications. You already have the ability to find these in Ubuntu Software, where they appear alongside the regular versions. You need to examine the source of what you are installing carefully. That's shown at the bottom of the application's page when you click on a search result.

_Or, use the terminal to find and install_:
```
dmn@Erica:~$ snap search gimp
Name                    Version  Publisher        Notes  Summary
gimp                    2.10.24  snapcrafters     -      GNU Image Manipulation Program

```
If you want to install this version 2.10.24, 
```
snap install gimp
```

That's all there is to it. You can then remove the one you have, or they can live together without any problem.

There's another option for newer versions called Flatpak. If you want to look into those, do some web investigation. They are also popular. It's too big a topic for a forum post here.

---

### Post by jmichaels29 on 2021-10-17
OK, thanks so much for the information.

I'm curious.  Is the latest version, of most programs, the same in Ubuntu Software Center and Synaptic Package Manager.  Do they pull from the same pool ?

---

### Post by guiverc on 2021-10-17
You didn't provide release details, but I'm betting you're on *focal* or 20.04.

```
guiverc@d960-ubu2:~/uwn/issues/704$   rmadison gimp
 gimp | 2.8.10-0ubuntu1   | trusty                   | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 gimp | 2.8.10-0ubuntu1.2 | trusty-security          | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 gimp | 2.8.10-0ubuntu1.2 | trusty-updates           | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 gimp | 2.8.16-1ubuntu1   | xenial/universe          | source, amd64, arm64, armhf, i386, powerpc, ppc64el, s390x
 gimp | 2.8.16-1ubuntu1.1 | xenial-security/universe | source, amd64, arm64, armhf, i386, powerpc, ppc64el, s390x
 gimp | 2.8.16-1ubuntu1.1 | xenial-updates/universe  | source, amd64, arm64, armhf, i386, powerpc, ppc64el, s390x
 gimp | 2.8.22-1          | bionic/universe          | source, amd64, arm64, armhf, i386, ppc64el, s390x
 gimp | 2.10.18-1         | focal/universe           | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 gimp | 2.10.22-3         | hirsute/universe         | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 gimp | 2.10.24-2         | impish/universe          | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 gimp | 2.10.24-2         | jammy/universe           | source, amd64, arm64, armhf, ppc64el, riscv64, s390x

```

If I `apt-cache policy` check mine - it'll report the 2.10.24-2 as I'm running *jammy* and that's the most up-to-date version my system will see (*actually it's likely the only version my system will see*!)

The command `sudo apt update` updates software lists for the sources you have enabled.. and doesn't go to what's available in other releases. If you start adding sources for another release; you'll soon find yourself in *dep* hell & with loads of problems, unless you're very careful & learn '[pinning]("https://help.ubuntu.com/community/PinningHowto")' though personally I find moving off the LTS cycle & just using the latest *stable* (non-LTS) release far easier..  though of course using *snap* or non-*deb* packages works too !

---

### Post by jmichaels29 on 2021-10-17
I just noticed, that I didn't really explore the Ubuntu Software Center fully, that I can click on the upper right and access Snap Store, where Gimp 2.10.24 and Gimp 2.10.28 are both available (again, both in Snap Store)....

I had an issue with 2.10.24 not saving EXIF data for my particular camera brand.  I will give 2.10.28 a try....

I have no idea what Ubuntu Focal Universe vs Snap Store is, or what either are, but I see Snap Store has options...I don't see such options in Synaptic Package Manager program...

thanks

---

### Post by guiverc on 2021-10-18
Synaptic Package Manager is a [*deb*] package manager (*as it's name implies*) so it can only deal with *deb* packages, just like `aptitude`, `Muon` or other like Package Manager programs.  They also only see packages available in your current sources (`/etc/apt/sources.list` & lists found in `/etc/apt/sources.list.d/`).

Software Stores (like Snap Store, Discover, Software Boutique etc) usually offer packages/applications from lists, which may be from different sources and include different package types (*but are limited to whatever is on their lists too, but you don't have control of these lists unlike the sources package managers work from*).

'**universe**' is a Ubuntu repository (see [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for more details); where 'main' is the main archive which has 5 years of support for LTS releases; however 'universe' packages are community sourced packages that come with shorter life-spans; eg. 3 years is the normal for LTS releases (some are just 9 months though; eg. not all *flavors* were LTS with 18.04 with Ubuntu Studio packages only coming with 9 months of support as was reported in the*release notes* & [notices]("https://fridge.ubuntu.com/2018/04/27/ubuntu-18-04-lts-bionic-beaver-released/").

I'm running Lubuntu *jammy* (*what will be 22.04 on release in six months*); so my base system is a standard Ubuntu one, but I have packages from the Lubuntu team which are found in 'universe' (community repository) that give me my LXQt desktop.  This box has multiple desktops installed; as I also have Xfce (Xubuntu) which is also found in 'universe', as well as GNOME (Ubuntu) which has its packages in the 'main' repository (the 'main' packages go through a ~*stricter* security audit than *universe* do).

We're all learning... Me I just wish I could retain a greater % of what I learn. :)

---

### Post by jmichaels29 on 2021-10-18
Thanks.  Thread marked as solved....

---

