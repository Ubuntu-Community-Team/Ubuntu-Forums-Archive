---
title: "Trusty dpkg error?"
date: 2014-05-23
forum: General Help
---

### Post by kansasnoob on 2014-05-23
No idea what happened here but I'd just completed a fresh install of Ubuntu Trusty i386, booted the new OS w/o a problem, then began to apply the updates that had been downloaded during installation. At that point I went and shaved, but upon my return the whole desktop was frozen - couldn't even bring up a TTY so I rebooted.

Now when I run apt-get update I'm told to run "sudo dpkg --configure -a" which tells me this:

```
dpkg: error: parsing file '/var/lib/dpkg/updates/0009' near line 0:
 newline in field name `openrisc/include/asm/bitops/__ffs.h'

```

I've googled a bit but I'm clueless what to do next :(

---

### Post by Zorael on 2014-05-23
Quoth [this askubuntu question](http://askubuntu.com/questions/527/what-is-stored-in-the-var-lib-dpkg-updates-folder);
> During the update dpkg stores status of the installation/update [in /var/lib/dpkg/updates]. This is how an incomplete installation process can be detected and decided what are the next packages going to be installed, So that the system can ask to use dpkg-configure -a if anything happens before completing installation or update.

Normally after a successful installation, the directory should be empty.

Very likely that **0009** file (and perhaps more beside it) is incomplete or corrupt.

I would try to move it out of there and try restarting the update process entirely. Do note that your system is possibly in an invalid state right now (package-wise), so at your own risk.
```
$ mkdir ~/update-backups
$ sudo mv /var/lib/dpkg/updates/**0009** ~/update-backups   # repeat for files other than 0009 if needed, or simply ***** to move them all
$ sudo dpkg --configure -a
$ sudo apt-get upgrade
```

---

### Post by kansasnoob on 2014-05-23
> **Zorael said:**
> Quoth [this askubuntu question](http://askubuntu.com/questions/527/what-is-stored-in-the-var-lib-dpkg-updates-folder);


Very likely that **0009** file (and perhaps more beside it) is incomplete or corrupt.

I would try to move it out of there and try restarting the update process entirely. Do note that your system is possibly in an invalid state right now (package-wise), so at your own risk.
```
$ mkdir ~/update-backups
$ sudo mv /var/lib/dpkg/updates/**0009** ~/update-backups   # repeat for files other than 0009 if needed, or simply ***** to move them all
$ sudo dpkg --configure -a
$ sudo apt-get upgrade
```

I had to repeat that for "/var/lib/dpkg/updates/0010" but otherwise that got me back on track :D

Thank you.

---

