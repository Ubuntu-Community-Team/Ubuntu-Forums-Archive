---
title: "[SOLVED] Updating Kubuntu Feisty To Gutsy"
date: 2007-08-18
forum: General Help
---

### Post by Vince4Amy on 2007-08-18
I'm trying to upgrade Kubuntu Feisty to Gutsy, how can I do this on Kubuntu, I know it's easy to do on Ubuntu (Gnome), but I can't seem to find a way to do this on Kubuntu.

---

### Post by g2g591 on 2007-08-18
adept_manager --dist-upgrade
or if that doesn't work adept_manger --dist-upgrade-devel

---

### Post by Vince4Amy on 2007-08-18
It didn't work unfortunatly:

```
adept_manager: Unknown option '--dist-upgrade-devel'.
```

Edit ```
adept_manager --version-upgrade
```

That works.

---

### Post by TheWizzard on 2007-08-18
can't you use the gnome update manager? 

```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install update-manager
gksudo "update-manager -d"
```

i'm not sure if this works

in kubuntu you should be able to just aptitude dist-upgrade
but this is considered less save

---

### Post by Vince4Amy on 2007-08-18
> 
adept_manager --version-upgrade

That works.


It didn't work in the end. 

Running sudo aptitude dist-upgrade results in:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

Edit:
Installing the Gnome Manager didn't work either. Just run that update manager clicked check & nothing new came up.

> warning: could not initiate dbus
current dist not found in meta-release file
could not send the dbus Inhibit signal: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


---

### Post by davidjmayo on 2007-08-18
from
[https://wiki.ubuntu.com/GutsyGibbon/Tribe4/Kubuntu](https://wiki.ubuntu.com/GutsyGibbon/Tribe4/Kubuntu)

For those of you who are using a prior stable release of Kubuntu and are wanting to upgrade or wait for Kubuntu 7.10 to become stable, well the Kubuntu developers have got a surprise for you. Now you will be able to easily upgrade with out going to the dreaded command line. If you are ready to upgrade now, and please remember that Kubuntu 7.10 (Gutsy) is an alpha release (see above warnings), simply press Alt + F2 and type kdesu "adept_manager --version-upgrade" if you are running Feisty (7.04) and kdesu "adept_manager --dist-upgrade-devel" if you already run a pre-release of Gutsy. Press the OK button or the Enter key to continue. When prompted for a password please enter your user password and press the OK button or the Enter key to continue. Once Adept has loaded and updated, in the top right hand corner you will see the Version Upgrade icon (two blue arrows stacked on top of each other) and the text. Press this button to launch the tool. Follow the instructions and reboot when completed. Enjoy your new Kubuntu 7.10 system!

---

### Post by Vince4Amy on 2007-08-18
Just found that page myself. Thanks. Updating now. Solved.

---

### Post by biodiesel-bri on 2007-10-27
Those quotes are significant.  The correct command is:

```
kdesu "adept_manager --version-upgrade"
```

---

