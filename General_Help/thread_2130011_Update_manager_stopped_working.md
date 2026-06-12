---
title: "Update manager stopped working"
date: 2013-03-28
forum: General Help
---

### Post by erichbuhler on 2013-03-28
I  am very dumb in Linux... I have tried to run the repair option in the Update Manager but does't repair anything.
I have tried the sudo **apt-get install -f** and get the following error:

Any idea? 
Thanks!!!


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-crystal libreoffice-style-hicontrast
The following packages will be upgraded:
  libreoffice-common
1 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.
11 not fully installed or removed.
Need to get 0 B/11.6 MB of archives.
After this operation, 12.3 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 241340 files and directories currently installed.)
Preparing to replace libreoffice-common 1:4.0.1~rc2-0ubuntu1~precise1~ppa1 (using .../libreoffice-common_1%3a4.0.2~rc1-0ubuntu1~precise2_all.deb) ...
Unpacking replacement libreoffice-common ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a4.0.2~rc1-0ubuntu1~precise2_all.deb (--unpack):
 trying to overwrite '/usr/lib/libreoffice/program/officehelper.py', which is also in package libreoffice-emailmerge 1:4.0.1~rc2-0ubuntu1~precise1~ppa1
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb (subprocess): subprocess data was killed by signal (Broken pipe)
dpkg-deb: error: subprocess <decompress> returned error exit status 2
rmdir: failed to remove `/var/lib/libreoffice/share/prereg/': No such file or directory
rmdir: failed to remove `/var/lib/libreoffice/share/': Directory not empty
rmdir: failed to remove `/var/lib/libreoffice/program/': No such file or directory
rmdir: failed to remove `/var/lib/libreoffice': Directory not empty
rmdir: failed to remove `/var/lib/libreoffice': Directory not empty
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a4.0.2~rc1-0ubuntu1~precise2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by plucky on 2013-03-28
> Preparing to replace libreoffice-common 1:4.0.1~rc2-0ubuntu1~precise1~ppa1 (using .../libreoffice-common_1%3a4.0.2~rc1-0ubuntu1~precise2_all.deb) ...

Do you have a libre-office PPA in your sources.list?

Have you installed a later version of libre-office using a PPA?

Post output for ```
cat /etc/apt/sources.list.d/*.list
```

My version is 1:3.5.7-0ubuntu4 on uptodate Precise 64-bit.

---

### Post by schragge on 2013-03-28
A LibreOffice 4.0.2 from [ppa:libreoffice/ppa]("https://launchpad.net/%7Elibreoffice/+archive/ppa") or from [ppa:libreoffice/libreoffice-4-0]("https://launchpad.net/%7Elibreoffice/+archive/libreoffice-4-0") conflicts with already installed LibreOffice 4.0.1. They cannot be installed in parallel. Remove the installed version:
```

dpkg --get-selections libreoffice\*|sed 's/\<install$/deinstall/'|sudo dpkg --set-selections
sudo dpkg -ra
sudo apt-get -f install

```

---

### Post by erichbuhler on 2013-03-30
> **schragge said:**
> A LibreOffice 4.0.2 from [ppa:libreoffice/ppa]("https://launchpad.net/%7Elibreoffice/+archive/ppa") or from [ppa:libreoffice/libreoffice-4-0]("https://launchpad.net/%7Elibreoffice/+archive/libreoffice-4-0") conflicts with already installed LibreOffice 4.0.1. They cannot be installed in parallel. Remove the installed version:
```

dpkg --get-selections libreoffice\*|sed 's/\<install$/deinstall/'|sudo dpkg --set-selections
sudo dpkg -ra
sudo apt-get -f install

```

Thank you! Worked perfectly !!!

---

