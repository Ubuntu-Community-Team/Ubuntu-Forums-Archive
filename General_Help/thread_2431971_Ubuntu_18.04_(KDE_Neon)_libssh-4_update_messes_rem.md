---
title: "Ubuntu 18.04 (KDE Neon): libssh-4 update messes remmina and x2go-client"
date: 2019-11-25
forum: General Help
---

### Post by timonoj on 2019-11-25
Hi guys!

Last week a libssh-4 update got several dependencies messed up, removing both remmina and x2go from my laptop. Now I can't install it again due to broken dependencies. What can I do?

There is this bug filed and closed, but its super unhelpful and I don't see any fix or workaround:
[https://bugs.kde.org/show_bug.cgi?id=414382](https://bugs.kde.org/show_bug.cgi?id=414382)

Thanks!

```
sudo apt install x2goclient 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Starting pkgProblemResolver with broken count: 1
Starting 2 pkgProblemResolver with broken count: 1
Investigating (0) libssh-4:amd64 < 0.9.0-1+18.04+bionic+build1 @ii mK Ib >
Broken libssh-4:amd64 Breaks on x2goclient:amd64 < none -> 4.1.1.1-2 @un puN > (< 4.1.2.1-1+)
  Considering x2goclient:amd64 9997 as a solution to libssh-4:amd64 8
  Removing libssh-4:amd64 rather than change x2goclient:amd64
Investigating (0) libssh-dev:amd64 < 0.9.0-1+18.04+bionic+build1 @ii mK Ib >
Broken libssh-dev:amd64 Depends on libssh-4:amd64 < 0.9.0-1+18.04+bionic+build1 @ii mR > (= 0.9.0-1+18.04+bionic+build1)
  Considering libssh-4:amd64 8 as a solution to libssh-dev:amd64 0
  Removing libssh-dev:amd64 rather than change libssh-4:amd64
Investigating (1) x2goclient:amd64 < none -> 4.1.1.1-2 @un puN Ib >
Broken x2goclient:amd64 Depends on libssh-4:amd64 < 0.9.0-1+18.04+bionic+build1 @ii mR > (>= 0.7.3)
  Considering libssh-4:amd64 8 as a solution to x2goclient:amd64 9997
  Added libssh-4:amd64 to the remove list
  Fixing x2goclient:amd64 via keep of libssh-4:amd64
Investigating (1) libssh-4:amd64 < 0.9.0-1+18.04+bionic+build1 @ii mK Ib >
Broken libssh-4:amd64 Breaks on x2goclient:amd64 < none -> 4.1.1.1-2 @un puN > (< 4.1.2.1-1+)
  Considering x2goclient:amd64 9997 as a solution to libssh-4:amd64 8
  Removing libssh-4:amd64 rather than change x2goclient:amd64
Investigating (2) x2goclient:amd64 < none -> 4.1.1.1-2 @un puN Ib >
Broken x2goclient:amd64 Depends on libssh-4:amd64 < 0.9.0-1+18.04+bionic+build1 @ii mR > (>= 0.7.3)
  Considering libssh-4:amd64 8 as a solution to x2goclient:amd64 9997
  Added libssh-4:amd64 to the remove list
  Fixing x2goclient:amd64 via keep of libssh-4:amd64
Investigating (2) libssh-4:amd64 < 0.9.0-1+18.04+bionic+build1 @ii mK Ib >
Broken libssh-4:amd64 Breaks on x2goclient:amd64 < none -> 4.1.1.1-2 @un puN > (< 4.1.2.1-1+)
  Considering x2goclient:amd64 9997 as a solution to libssh-4:amd64 9997
  Removing libssh-4:amd64 rather than change x2goclient:amd64
Investigating (3) x2goclient:amd64 < none -> 4.1.1.1-2 @un puN Ib >
Broken x2goclient:amd64 Depends on libssh-4:amd64 < 0.9.0-1+18.04+bionic+build1 @ii mR > (>= 0.7.3)
  Considering libssh-4:amd64 9997 as a solution to x2goclient:amd64 9997
  Considering libssh-4:amd64 9997 as a solution to x2goclient:amd64 9997
  Considering libssh-4:amd64 9997 as a solution to x2goclient:amd64 9997
Investigating (3) kio-extras:amd64 < 4:19.08.3-0xneon+18.04+bionic+build38 @ii mK Ib >
Broken kio-extras:amd64 Depends on libssh-4:amd64 < 0.9.0-1+18.04+bionic+build1 @ii mR >
  Considering libssh-4:amd64 9997 as a solution to kio-extras:amd64 16
  Removing kio-extras:amd64 rather than change libssh-4:amd64
Investigating (3) neon-desktop:amd64 < 4+p18.04+git20191119.1212 @ii mK NPb Ib >
Broken neon-desktop:amd64 Depends on kio-extras:amd64 < 4:19.08.3-0xneon+18.04+bionic+build38 @ii mR >
  Considering kio-extras:amd64 9997 as a solution to neon-desktop:amd64 0
  Removing neon-desktop:amd64 rather than change kio-extras:amd64
Investigating (4) x2goclient:amd64 < none -> 4.1.1.1-2 @un puN Ib >
Broken x2goclient:amd64 Depends on libssh-4:amd64 < 0.9.0-1+18.04+bionic+build1 @ii mR > (>= 0.7.3)
  Considering libssh-4:amd64 9997 as a solution to x2goclient:amd64 9997
  Considering libssh-4:amd64 9997 as a solution to x2goclient:amd64 9997
  Considering libssh-4:amd64 9997 as a solution to x2goclient:amd64 9997
Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 x2goclient : Depends: libssh-4 (>= 0.7.3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by speartip on 2019-11-25
Probably best to post on the KDE Neon forums. This is the problem with Neon, they constantly update the KDE packages, but this can occasionally cause conflicts with Ubuntu's packages. For this reason I have now gone back to Kubuntu with the Backports enabled.

---

### Post by timonoj on 2019-11-25
Hmmm aren't the packages involved (libssh-4, remmina and x2go) all belonging to Ubuntu repo anyway? They're not related to the KDE desktop I believe. Is people on 18.04 affected as well?

---

### Post by speartip on 2019-11-25
True, they are all in the Ubuntu repo, but they also pull in dependencies. It only takes one that may be updated by Neon, to balk the installation. I've just tested on Kubuntu 18.04 & x2goclient installs fine.
The problem is indeed the libssh-4 package. In Kubuntu the version is 0.8.0. In Neon it's 0.9.0.
If you using Muon Package Manager, highlight the libssh-4 package, click on "Versions" & see if the 0.8.0 package is still there to be reinstalled. Be careful though, downgrading it may break other packages.

---

### Post by timonoj on 2019-11-25
> **speartip said:**
> True, they are all in the Ubuntu repo, but they also pull in dependencies. It only takes one that may be updated by Neon, to balk the installation. I've just tested on Kubuntu 18.04 & x2goclient installs fine.
The problem is indeed the libssh-4 package. In Kubuntu the version is 0.8.0. In Neon it's 0.9.0.
If you using Muon Package Manager, highlight the libssh-4 package, click on "Versions" & see if the 0.8.0 package is still there to be reinstalled. Be careful though, downgrading it may break other packages.

Great...thanks, you're on point with your information. Libssh-4 is currently on 0.9.0-1+18.04+bionic+build1. But I'm using Neon's package manager, Discover, which doesn't give options to choose other versions of a package. Is there a command line to do the same?

EDIT: Nevermind, when you can ask a basic question, you can also google it...less hassle for everyone.

To list available versions:
```
apt-cache showpkg libssh-4 
```

Then in my case seems the previous most recent version is:
```
sudo apt install libssh-4=0.8.0~20170825.94fa1e38-1ubuntu0.2
```

After this, I can successfully install again my x2goclient :)
But of course, now ubuntu wants to immediately update the package...so finally:
```
sudo apt-mark hold libssh-4
```
In order to hold the library at the current version, at least for the time being.


Thanks!

---

### Post by speartip on 2019-11-25
Best thing is just to install muon. If its a recent update the old package should still be there, unless you clean out apt & your cache regularly. Discover isn't Neon specific, it's also used in Kubuntu, but I prefer to use either muon or synaptic to install/uninstall programs. You get more info about the package & dependencies & issues like this than you get with Discover.

---

### Post by timonoj on 2019-11-25
> **speartip said:**
> Best thing is just to install muon. If its a recent update the old package should still be there, unless you clean out apt & your cache regularly. Discover isn't Neon specific, it's also used in Kubuntu, but I prefer to use either muon or synaptic to install/uninstall programs. You get more info about the package & dependencies & issues like this than you get with Discover.

Thanks...for the moment I fixed it this way, but yes, I'm going to install Muon. I never liked discover anyway.

---

