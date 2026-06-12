---
title: "Problems with HAL and DBUS in Kubuntu when upgrade to KDE4 repo"
date: 2008-01-20
forum: General Help
---

### Post by mzw! on 2008-01-20
Hi!!
I just added the repo to try KDE4 from the instructions in kubuntu.org
```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu gutsy main
```

I did apt-get update and dist-upgrade and some packages such us kdebase* etc were upgraded.

The thing is that now I in kde3, and with amarok when I try to sync with my ipod, no devices are detected.

When I try to autodetect devices, it pops up this:

```
No new media devices were found. If you feel this is an error, ensure that the DBUS and HAL daemons are running and KDE was built with support for them. You can test this by running "dcop kded mediamanager fullList" in a Konsole window
```

Anybody having the same issue?

Thank you for your help!!

---

### Post by utUtu on 2008-01-21
> **mzw! said:**
> Hi!!
I just added the repo to try KDE4 from the instructions in kubuntu.org
```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu gutsy main
```

I did apt-get update and **dist-upgrade **and some packages such us kdebase* etc were upgraded.
.....
Thank you for your help!!

Apparently you did not follow the instructions.  After adding the repo, do an update and then install **kde4-core**

---

### Post by mzw! on 2008-01-27
I did install kde4-core, but I mean, when running kde3, for example in Amarok the ipod is not recognized.

The main packages for kde3 are upgraded to the ppa version and they happen to have something wrong with hal or dbus... or at least amarok says that.

I downgraded those packages to the official repositories and I have not got that problem.

---

