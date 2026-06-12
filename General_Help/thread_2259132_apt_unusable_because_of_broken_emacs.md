---
title: "apt unusable because of broken emacs?"
date: 2015-01-02
forum: General Help
---

### Post by philip-t on 2015-01-02
Dear all,

We're having problem with a trusty installation we want to upgrade. No matter what package we want to install or upgrade (or if we do sudo apt-get upgrade), we get these errors related to an emacs24 installation:

------------------------------------------------------------------------------------------------------------------------------------------------------------
$ sudo apt-get install emacs24-bin-common 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
emacs24-bin-common is already the newest version.
emacs24-bin-common set to manually installed.
The following packages will be upgraded:
  emacs24
1 upgraded, 0 newly installed, 0 to remove and 211 not upgraded.
6 not fully installed or removed.
Need to get 0 B/2,859 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
(Reading database ... 1036324 files and directories currently installed.)
Preparing to unpack .../emacs24_24.3+1-2ubuntu1_i386.deb ...
dpkg-query: error: --status needs a valid package name but '#auctex#' is not: illegal package name in specifier '#auctex#': must start with an alphanumeric character


Use --help for help about querying packages.
emacsen-common: dpkg invocation failed at /usr/lib/emacsen-common/lib.pl line 80.
dpkg: warning: subprocess old pre-removal script returned error exit status 2
dpkg: trying script from the new package instead ...
dpkg-query: error: --status needs a valid package name but '#auctex#' is not: illegal package name in specifier '#auctex#': must start with an alphanumeric character


Use --help for help about querying packages.
emacsen-common: dpkg invocation failed at /usr/lib/emacsen-common/lib.pl line 80.
dpkg: error processing archive /var/cache/apt/archives/emacs24_24.3+1-2ubuntu1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
update-alternatives: using /usr/bin/emacs24-x to provide /usr/bin/emacs (emacs) in auto mode
dpkg-query: error: --status needs a valid package name but '#auctex#' is not: illegal package name in specifier '#auctex#': must start with an alphanumeric character


Use --help for help about querying packages.
emacsen-common: dpkg invocation failed at /usr/lib/emacsen-common/lib.pl line 80.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/emacs24_24.3+1-2ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
-----------------------------------------------------------------------------------------------------------------------------------------------------

We have tried to remove everything related to emacs which fails too. Also we tried "sudo apt-get -f install" with no package specification. Same error.

Thanks a lot guys. I apologize for asking for help with such an out of date installation.
- John

---

### Post by schragge on 2015-01-02
Trusty is not outdated at all. It's the current LTS (long time support) release. Yep, it looks like a bug in one of maintainer script of emacs. The script in question is */var/lib/dpkg/info/emacsen-common.prerm*. It calls /usr/lib/emacsen-common/emacs-package-remove, which in turn uses functions from /usr/lib/emacsen-common/lib.pl.

Try to run this script manually:
```
sudo /var/lib/dpkg/info/emacsen-common.prerm
``` If it fails with the same error message, try this dirty hack:
```
sudo -i '/emacs-package-remove/s/$/||:/' /var/lib/dpkg/info/emacsen-common.prerm
```
After that
```
sudo apt-get install -f
```
Then purge everything related to emacs:
```
sudo apt-get purge 'emac[s]'
```

---

### Post by philip-t on 2015-01-25
Dear Shragge,

First of all, thank you very much for your reply and I apologize for this late reply. Using your hints, the problem was resolved.

The user had been editing one of the emacs install/uninstall scripts in apt and hence unknowingly created "#" and "~" autosave files. These filenames were somehow interpreted by apt leading it to search for unexisting packages. After removal of these autosave files, the system was working again.

Thank you very much for taking your time to help us with this - to us - very confusing error.

Kind regards,
John

---

