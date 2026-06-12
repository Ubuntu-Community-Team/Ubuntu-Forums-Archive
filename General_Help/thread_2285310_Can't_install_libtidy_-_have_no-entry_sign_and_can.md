---
title: "Can't install libtidy - have no-entry sign and can't install new packages"
date: 2015-07-04
forum: General Help
---

### Post by James Wilde on 2015-07-04
I have the no-entry sign in my Ubuntu 14-04 and can't seem to get rid of it.  This appeared after installing Calibre from the software centre.  Trying to uninstall Calibre isn't working.  I have a suspicion that I'm in catch 22, in that the problem package, libtidy-0.99-0, is needed to correct the problem.  Here's what I get from sudo apt-get -f install <with or without the package name>:

```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  kde-l10n-engb kde-l10n-is kde-l10n-sv kde-l10n-zhcn lib32z1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libtidy-0.99-0
The following NEW packages will be installed
  libtidy-0.99-0
0 to upgrade, 1 to newly install, 0 to remove and 16 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/119 kB of archives.
After this operation, 415 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 635399 files and directories currently installed.)
Preparing to unpack .../libtidy-0.99-0_20091223cvs-1.2ubuntu1_amd64.deb ...
Unpacking libtidy-0.99-0 (20091223cvs-1.2ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libtidy-0.99-0_20091223cvs-1.2ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libtidy-0.99.so.0.0.0', which is also in package libtidy 20130211-git-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libtidy-0.99-0_20091223cvs-1.2ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I'd very much appreciate any help.  Haven't found this problem (with this package) in my search of the archives.

---

### Post by howefield on 2015-07-04
Try

```
sudo dpkg --remove libtidy
```

then try installing Calibre again, have you installed software from any non official Ubuntu repositories ?

---

### Post by James Wilde on 2015-07-08
Sorry it took so long to get back to you, and thanks, Howefield, for your input.

I ran the command and discovered that libtidy was a dependency of pirateplayer.  I removed pirateplayer and could then uninstall and reinstall libtidy.  I tidied up with apt-get autoremove and my no-entry sign disappeared.  So I'll remember that pirateplayer may need to be removed again if this crops up once more.

Thanks for solving this for me.

---

### Post by howefield on 2015-07-08
You're more than welcome, glad you are sorted.

---

