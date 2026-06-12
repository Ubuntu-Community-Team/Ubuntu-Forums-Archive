---
title: "broken package please help!"
date: 2007-05-01
forum: General Help
---

### Post by rainbowjoshua on 2007-05-01
Okay, so I'm trying to get my new printer ( a Brother MFC-440CN) to work, and wonderfully, Brother provides debian packages.  Of course, I tried to install them in the wrong order, and now one package is completely broken, it won't uninstall, install, configure, OR show up in synaptic.  Only dpkg and dselect show it.

dpkg -C reports:

The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 mfc440cncupswrapper  Brother CUPS PTouch Printer Definitions

---

I've tried every --force and other action I can find in the man page for dpkg.  Woud love any suggestions how I can remove this package to try to reinstall.  When I try to remove the package with:

 dpkg --force-all --purge mfc440cncupswrapper

reports:

dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 143397 files and directories currently installed.)
Removing mfc440cncupswrapper ...
/var/lib/dpkg/info/mfc440cncupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc440cn/cupswrapper/cupswrappermfc440cn: not found
dpkg: error processing mfc440cncupswrapper (--purge):
 subprocess pre-removal script returned error exit status 127
/var/lib/dpkg/info/mfc440cncupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc440cn/cupswrapper/cupswrappermfc440cn: not found
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 mfc440cncupswrapper


---

Which seems to be telling me to reinstall it before removing it, but I can't find any way to do that!  Help please!

Thank you,
Joshua

---

### Post by zvacet on 2007-05-01
```
sudo apt-get remove --purge file_name
```

---

### Post by ayoli on 2007-05-01
if purge do not works due to files not found
> ...Removing mfc440cncupswrapper ...
/var/lib/dpkg/info/mfc440cncupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc440cn/cupswrapper/cupswrappermfc440cn: not found
dpkg: error processing mfc440cncupswrapper (--purge): ..
try to create them before like:
touch /path/of/file/you/want

btw, i'm sure apt/dpkg tools have a way to avoid these kind of problems, but i don't know them at the moment, so i give you an ugly solution :)

---

### Post by Zeke46 on 2007-07-08
The exact same thing happened to me.  I'm thinking reinstall is the only option at this point.  I can't run update-manager or Package Install.  I think it might work to remake all of the directories with the installation and fill it with dummy files, and then try uninstalling.  but i don't know all of the files and directories because mine are gone.  If someone were willing to install mfc440cncupswrapper.deb, and then tell what files are found under /usr/local/Brother/Printer/...... and file names... a lot of work yes, but i think it may work.


---

okay, do this commad:

$ sudo rm *mfc440cn*
...

and then reinstall it all from the beginning.

---

