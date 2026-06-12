---
title: "Installing, Uninstalling, and Updating Non-Package Programs"
date: 2014-08-29
forum: General Help
---

### Post by parkergking on 2014-08-29
Hey guys, been using Ubuntu for a few weeks, and there are a lot of things I really like about. However, there's also a lot of things that give me headaches..


One of the major hurdles I'm trying to get over is learning where to install, how and where to place paths, how to uninstall, and how to update programs that are not downloaded through the package manager.

An example of some of the programs I'm trying to use are things like, PhpStorm, Teamviewer, Firestorm Viewer, etc..


If anyone could shed some light on this, I would be extremely grateful. I really want to enjoy Ubuntu but these things are making it difficult at the moment..

Thanks in advance!

---

### Post by slooksterpsv on 2014-08-29
If they are .DEB packages you can remove them from the software center, to update just download the latest update and it'll overwrite the installation.

If you manually compiled them and installed them, that's different, because there's no package to tell what specifically installed, you'll have to locate where it installed and remove manually. Example: my efibootorder app installs to the following locations:
```

shawn@shawn-Satellite-C75D-A:~$ locate efibootorder | grep usr
/usr/bin/efibootorder
/usr/share/efibootorder
/usr/share/applications/efibootorder.desktop
/usr/share/doc/efibootorder
/usr/share/doc/efibootorder/changelog.Debian.gz
/usr/share/doc/efibootorder/copyright
/usr/share/efibootorder/efibootorder
/usr/share/efibootorder/efibootorder-icon.png

```

It's best, that if you manually compile and install an app, to put it in the /opt directory - you can find literature on compiling and putting apps in specific locations by searching.

You can locate some info about where you installed your items by opening a terminal and running:
```

sudo locate *name_of_program*

```

But it's best to install using DEBs until you feel comfortable navigating the file system with terminal.

EDIT:

You can also remove via terminal with a few different options:
sudo apt-get remove *name_of_app*

Example:
sudo apt-get remove google-chrome-stable

Or:
sudo dpkg -r *name_of_app*

Example:
sudo dpkg -r google-chrome-stable

---

### Post by ian-weisser on 2014-08-30
> **parkergking said:**
>  learning where to install, how and where to place paths, how to uninstall, and how to update programs that are not downloaded through the package manager.

An example of some of the programs I'm trying to use are things like, PhpStorm, Teamviewer, Firestorm Viewer, etc..

Well, you can muck about with manual installs if you wish, but easier alternatives are available...
PhpStorm and Firestorm Viewer are available from PPAs. Any good search engine will tell you which repositories to add and how to add them..
Teamviewer .deb files are available from the Teamviewer website. Double click on the downloaded file to install.

They are non-Ubuntu software (not from the official Ubuntu Repositories).
 You should uninstall all non-Ubuntu software before you upgrade to the next release of Ubuntu (14.10, 16.04, etc). Non-Ubuntu software can occasionally break release upgrades if a similarly-named package is in the new release repositories.

Normal daily upgrades to the PPA, if any, are provided through System Updater by the volunteer PPA maintainers.
Teamviewer updates, if any, may come from Teamviewer though several possible mechanism.
Non-Ubuntu software does not receive updates (including security updates) from Ubuntu.

All PPA and .deb software can be uninstalled using Software Center or any other package manager frontend (apt-get, synaptic, etc.)

---

