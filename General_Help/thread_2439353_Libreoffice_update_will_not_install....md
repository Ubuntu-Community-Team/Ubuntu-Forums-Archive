---
title: "Libreoffice update will not install..."
date: 2020-03-26
forum: General Help
---

### Post by timgood on 2020-03-26
Updates available - mainly LibreOffice, but error when attempting to install them:

Fatal error: Error while installing package: trying to overwrite '/usr/lib/libreoffice/share/config/soffice.cfg/modules/smath/menubar/menubar.xml', which is also in package libreoffice-common 1

Trying to remedy with 'sudo apt --fix-broken install:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Starting pkgProblemResolver with broken count: 0
Starting 2 pkgProblemResolver with broken count: 0
Done
 Done
Starting pkgProblemResolver with broken count: 0
Starting 2 pkgProblemResolver with broken count: 0
Done
The following additional packages will be installed:
  libjuh-java libjurt-java libreoffice-common libreoffice-java-common libreoffice-math libreoffice-report-builder libreoffice-script-provider-bsh libreoffice-script-provider-js libreoffice-script-provider-python libreoffice-style-colibre
  libreoffice-style-elementary libridl-java libuno-cppu3 libuno-cppuhelpergcc3-3 libuno-purpenvhelpergcc3-3 libuno-sal3 libuno-salhelpergcc3-3 libunoil-java libunoloader-java uno-libs-private
The following packages will be REMOVED
  uno-libs3
The following NEW packages will be installed
  libjuh-java libjurt-java libridl-java libuno-cppu3 libuno-cppuhelpergcc3-3 libuno-purpenvhelpergcc3-3 libuno-sal3 libuno-salhelpergcc3-3 libunoil-java libunoloader-java uno-libs-private
The following packages will be upgraded:
  libreoffice-common libreoffice-java-common libreoffice-math libreoffice-report-builder libreoffice-script-provider-bsh libreoffice-script-provider-js libreoffice-script-provider-python libreoffice-style-colibre libreoffice-style-elementary
9 to upgrade, 11 to newly install, 1 to remove and 3 not to upgrade.
21 not fully installed or removed.
Need to get 0 B/42.3 MB of archives.
After this operation, 32.8 MB disk space will be freed.
Do you want to continue? [Y/n] 

Then:
(Reading database ... 270689 files and directories currently installed.)
Preparing to unpack .../libreoffice-math_1%3a6.4.2-0ubuntu0.18.04.2_amd64.deb ...
Unpacking libreoffice-math (1:6.4.2-0ubuntu0.18.04.2) over (1:6.3.5~rc2-0ubuntu0.18.04.1~lo1) ...
dpkg: error processing archive /var/cache/apt/archives/libreoffice-math_1%3a6.4.2-0ubuntu0.18.04.2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libreoffice/share/config/soffice.cfg/modules/smath/menubar/menubar.xml', which is also in package libreoffice-common 1:6.3.5~rc2-0ubuntu0.18.04.1~lo1
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Restoring backup of /usr/share/doc/libreoffice-math ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-math_1%3a6.4.2-0ubuntu0.18.04.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Now LibreOffice will not start at all.

Any ideas?

---

### Post by Impavidus on 2020-03-26
So, a file that is in libreoffice-common in version 6.3.5 is in libreoffice-math in version 6.4.2. The full version string suggests you use Ubuntu 18.04, which comes with Libreoffice 6.0.7. Do you use a PPA for Libreoffice?

Anyway, one thing you could try is to remove Libreoffice, then reinstall it. Although upgrading libreoffice-common before upgrading libreoffice-math might do the trick too.

---

### Post by benaventeadrian on 2020-03-26
This worked for me:
```

sudo apt clean
sudo apt autoclean
sudo apt-get install -f

```

---

### Post by arvana2 on 2020-03-26
I had the same issue.  Using the LibreOffice Fresh PPA.

Tried the suggested solutions.  Also tried manually deleting /usr/lib/libreoffice/share/config/soffice.cfg/modules/smath/menubar/menubar.xml and re-running updates.

The only thing that worked for me was uninstalling and reinstalling LibreOffice.  Hopefully someone can come up with a more elegant solution, or the PPA gets fixed.

---

### Post by benjamin-gemmill on 2020-03-26
What worked for me:
```
sudo aptitude -f remove libreoffice-math
```
(if you use math install it again afterwards)

An important thing to note is aptitude gives up much less easily than apt and apt-get do.

It looks like a file was moved from one package to the other between versions, and upgrading by default picks an order where the file conflicts. Removing one of the two packages will let the upgrade go through.

---

### Post by manuel-schulte on 2020-03-27
Hi Folks,
The solution is here: [https://askubuntu.com/a/1220556/309328](https://askubuntu.com/a/1220556/309328)
It saved my day!
Cheers,
Manuel

---

