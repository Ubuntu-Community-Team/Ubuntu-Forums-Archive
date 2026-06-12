---
title: "Software Index broken this morning"
date: 2007-03-28
forum: General Help
---

### Post by plb on 2007-03-28
It then tells me to sudo apt-get -f install which results in:

```
plb@plb-desktop:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libxcomposite1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  openoffice.org-common
Recommended packages:
  openoffice.org-style-crystal openoffice.org-style-hicontrast
The following packages will be upgraded:
  openoffice.org-common
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
21 not fully installed or removed.
Need to get 0B/11.4MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 113052 files and directories currently installed.)
Preparing to replace openoffice.org-common 2.0.4-0ubuntu4 (using .../openoffice.org-common_2.0.4-0ubuntu5_all.deb) ...
Unpacking replacement openoffice.org-common ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/openoffice.org-common_2.0.4-0ubuntu5_all.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/share/template/wizard/letter/es/pri-bottle_l.ott')
***
* Updating MIME database in /usr/share/mime...
Wrote 481 strings at 20 - 27f8
Wrote aliases at 27f8 - 29ac
Wrote parents at 29ac - 337c
Wrote literal globs at 337c - 33e0
Wrote suffix globs at 33e0 - 6778
Wrote full globs at 6778 - 679c
Wrote magic at 679c - bdac
Wrote namespace list at bdac - bdbc
***
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-common_2.0.4-0ubuntu5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Anyone else getting this? Edgy BTW

---

### Post by plb on 2007-03-28
"Fix Broken Packages" though synaptic also didn't work...is no one else getting this?

---

### Post by AndyCooll on 2007-03-28
Well ...not exactly the same messages, however yes I too am having problems with todays upgrades with messages along the lines of certain packages not being upgraded.

:cool:

---

### Post by plb on 2007-03-28
Figured out the problem...removed the packages from apt/archives then ran apt-get update and upgrade.

---

