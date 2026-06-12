---
title: "Can't install libreofice unmet dependecies! have tried other threads, didnt work"
date: 2016-07-24
forum: General Help
---

### Post by Karolina.K on 2016-07-24
Hello

I uninstalled libreoffice to install openoffice (wanted to try it) and now decided i like libre office much better, so i did "sudo apt-get purge openoffice*  and only to be greeted by this when trying to install libreoffice again:

```
#Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice : Depends: fonts-sil-gentium-basic but it is not going to be installed
               Depends: libreoffice-base but it is not going to be installed
               Depends: libreoffice-calc but it is not going to be installed
               Depends: libreoffice-draw but it is not going to be installed
               Depends: libreoffice-impress but it is not going to be installed
               Depends: libreoffice-report-builder-bin but it is not going to be installed
               Depends: libreoffice-avmedia-backend-gstreamer but it is not going to be installed
               Depends: libreoffice-java-common (>= 1:5.1.4~) but it is not going to be installed
               Recommends: libreoffice-gnome but it is not going to be installed or
                           libreoffice-kde but it is not going to be installed
 libreoffice-core : Depends: libreoffice-common (> 1:5.1.4) but it is not going to be installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-ja : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-sv : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-zh-tw : Depends: libreoffice-common but it is not going to be installed
 libreoffice-style-elementary : Depends: libreoffice-common (= 1:5.1.4-0ubuntu1) but it is not going to be installed
 libreoffice-style-galaxy : Depends: libreoffice-common (= 1:5.1.4-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).#
```

I have tried all threads i could find about solving this problem, but nothing helped . help me ubuntu forums, you're my only hope!

---

### Post by wildmanne39 on 2016-07-24
Have you tried ```
sudo apt-get -f install
```
like it suggests.

---

### Post by Karolina.K on 2016-07-24
yes :( it doesn't work either, it gives this output:

```
#The following NEW packages will be installed:  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
18 not fully installed or removed.
Need to get 22,3 MB of archives.
After this operation, 84,8 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://gensho.acc.umu.se/ubuntu](http://gensho.acc.umu.se/ubuntu) xenial-updates/main amd64 libreoffice-common all 1:5.1.4-0ubuntu1 [22,3 MB]
Fetched 22,3 MB in 18s (1 225 kB/s)                                                                                                 
(Reading database ... 509095 files and directories currently installed.)
Preparing to unpack .../libreoffice-common_1%3a5.1.4-0ubuntu1_all.deb ...
Unpacking libreoffice-common (1:5.1.4-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a5.1.4-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.1.2-9782
rmdir: failed to remove '/var/lib/libreoffice/share/prereg/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice/share/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice/program/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice': No such file or directory
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160701-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Processing triggers for gnome-icon-theme (3.12.0-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a5.1.4-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)#
```

---

### Post by wildmanne39 on 2016-07-24
I believe this will fix your issue please do:
```
sudo apt-get purge --remove openoffice-debian-menus
```
Then:
```
sudo apt-get -f install
```
Then try to install libreoffice again.

---

### Post by Karolina.K on 2016-07-24
Still doesnt work this is what the two commands gave as output:

#karolin@karolin-p6563sc:~$ sudo apt-get purge --remove openoffice-debian-menus[sudo] password for karolin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 ```
libreoffice-core : Depends: libreoffice-common (> 1:5.1.4) but it is not going to be installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-ja : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-sv : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-zh-tw : Depends: libreoffice-common but it is not going to be installed
 libreoffice-style-elementary : Depends: libreoffice-common (= 1:5.1.4-0ubuntu1) but it is not going to be installed
 libreoffice-style-galaxy : Depends: libreoffice-common (= 1:5.1.4-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
karolin@karolin-p6563sc:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  hunspell-sv-se hyphen-en-gb hyphen-sv kde-l10n-engb kde-l10n-ja kde-l10n-sv kde-l10n-zhtw kubuntu-debug-installer libapt-inst1.7
  libapt-pkg4.16 libbasicusageenvironment0 libboost-iostreams1.58.0 libcamel-1.2-52 libcdr-0.1-1 libck-connector0 libdns-export100
  libebook-contacts-1.2-1 libecal-1.2-18 libedata-cal-1.2-27 libedataserver-1.2-20 libenca0 libfreehand-0.1-1 libgif4
  libgnutls-deb0-28:i386 libgroupsock1 libirs-export91 libisc-export95 libisccfg-export90 libisl13 liblivemedia23 libllvm3.6v5
  libllvm3.6v5:i386 libmysqlclient18:i386 liborcus-0.10-0v5 libpagemaker-0.0-0 libpgm-5.1-0 libpoppler52 libpth20 libqapt3
  libqapt3-runtime libqpdf13v5 libreoffice-help-en-gb libreoffice-help-en-us libreoffice-help-ja libreoffice-help-sv
  libreoffice-help-zh-tw libreoffice-l10n-en-gb libreoffice-l10n-en-za libreoffice-l10n-ja libreoffice-l10n-sv
  libreoffice-l10n-zh-tw libsodium13 libunique-1.0-0 libusageenvironment1 libx265-59 libzmq3 linux-headers-4.2.0-17
  linux-headers-4.2.0-17-generic linux-headers-4.2.0-18 linux-headers-4.2.0-18-generic linux-headers-4.2.0-21
  linux-headers-4.2.0-21-generic linux-headers-4.2.0-35 linux-headers-4.2.0-35-generic linux-headers-4.4.0-18
  linux-headers-4.4.0-18-generic linux-headers-4.4.0-22 linux-headers-4.4.0-22-generic linux-headers-4.4.0-24
  linux-headers-4.4.0-24-generic linux-image-4.2.0-17-generic linux-image-4.2.0-18-generic linux-image-4.2.0-21-generic
  linux-image-4.2.0-35-generic linux-image-4.4.0-18-generic linux-image-4.4.0-22-generic linux-image-4.4.0-24-generic
  linux-image-extra-4.2.0-17-generic linux-image-extra-4.2.0-18-generic linux-image-extra-4.2.0-21-generic
  linux-image-extra-4.2.0-35-generic linux-image-extra-4.4.0-18-generic linux-image-extra-4.4.0-22-generic
  linux-image-extra-4.4.0-24-generic mythes-en-au mythes-sv python-cffi python-ply python-pycparser python-support python3-cffi
  python3-ply python3-pycparser qapt-batch ttf-dejavu-core
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-breeze libreoffice-style-hicontrast libreoffice-style-human libreoffice-style-oxygen libreoffice-style-sifr
  libreoffice-style-tango
The following NEW packages will be installed:
  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
18 not fully installed or removed.
Need to get 0 B/22,3 MB of archives.
After this operation, 84,8 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 509095 files and directories currently installed.)
Preparing to unpack .../libreoffice-common_1%3a5.1.4-0ubuntu1_all.deb ...
Unpacking libreoffice-common (1:5.1.4-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a5.1.4-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.1.2-9782
rmdir: failed to remove '/var/lib/libreoffice/share/prereg/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice/share/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice/program/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice': No such file or directory
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160701-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Processing triggers for gnome-icon-theme (3.12.0-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a5.1.4-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
karolin@karolin-p6563sc:~$ sudo apt-get install libreoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice : Depends: fonts-sil-gentium-basic but it is not going to be installed
               Depends: libreoffice-base but it is not going to be installed
               Depends: libreoffice-calc but it is not going to be installed
               Depends: libreoffice-draw but it is not going to be installed
               Depends: libreoffice-impress but it is not going to be installed
               Depends: libreoffice-report-builder-bin but it is not going to be installed
               Depends: libreoffice-avmedia-backend-gstreamer but it is not going to be installed
               Depends: libreoffice-java-common (>= 1:5.1.4~) but it is not going to be installed
               Recommends: libreoffice-gnome but it is not going to be installed or
                           libreoffice-kde but it is not going to be installed
 libreoffice-core : Depends: libreoffice-common (> 1:5.1.4) but it is not going to be installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-ja : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-sv : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-zh-tw : Depends: libreoffice-common but it is not going to be installed
 libreoffice-style-elementary : Depends: libreoffice-common (= 1:5.1.4-0ubuntu1) but it is not going to be installed
 libreoffice-style-galaxy : Depends: libreoffice-common (= 1:5.1.4-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
#
```

---

### Post by mc4man on 2016-07-24
try - 
```
sudo apt-get purge openoffice.org-*
```
if no better maybe describe how you install openoffice & from where

---

### Post by Karolina.K on 2016-07-24
no better :( I removed before libreoffice with the purge command, (some thread about removing it completly) then i downloaded openoffice via their official site , and installed it using software center.  using the file named Apache_OpenOffice_4.1.2_Linux_x86-64_install-rpm_en-US.tar.gz

---

### Post by wildmanne39 on 2016-07-24
That file you say you installed it from is a rpm file for like Red Hat linux and other distro's but not ubuntu, I do realize there is a way I believe to install it  on ubuntu but I do not know why you would when you can use a deb file that is made for ubuntu.

Link to where you got that file from please.
Please post every thing you have tried and the error messages.
Thanks

---

### Post by wildmanne39 on 2016-07-24
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Karolina.K on 2016-07-24
oh sorry, i remembered now that i did install the deb one, this one to be precise ```
 Apache_OpenOffice_4.1.2_Linux_x86-64_install-deb_en-US.tar.gz
```

---

### Post by mc4man on 2016-07-24
> **Karolina.K said:**
> oh sorry, i remembered now that i did install the deb one, this one to be precise ```
 Apache_OpenOffice_4.1.2_Linux_x86-64_install-deb_en-US.tar.gz
```
What's this report?
```
apt-cache policy openoffice*
```

---

### Post by Karolina.K on 2016-07-24
it reports this :     ```
 karolin@karolin-p6563sc:~$ apt-cache policy openoffice*openoffice-ogltrans:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice-writer:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice.org-debian-menus:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice-gnome-integration:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice.org-spellcheck-fr-fr:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-thesaurus-de-ch:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice-onlineupdate:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice.org-hyphenation-en-ca:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-hyphenation-en-us:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-updatedicts:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice-en-us-help:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice-ooolinguistic:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openofficeorg-desktop-integration:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-kde:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-common:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice-ure:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice-desktop-integration:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-spellcheck-an:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-spellcheck-ca:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-spellcheck-eo:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-spellcheck-es:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-spellcheck-eu:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-spellcheck-fo:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-spellcheck-gl:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice-debian-menus:
  Installed: 4.1.2-9782
  Candidate: 4.1.2-9782
  Version table:
 *** 4.1.2-9782 100
        100 /var/lib/dpkg/status
openoffice.org-spellcheck-nb:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-spellcheck-nn:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-spellcheck-nr:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-spellcheck-ns:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-spellcheck-ss:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-spellcheck-st:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-spellcheck-tl:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-spellcheck-tn:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-spellcheck-uz:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-spellcheck-ve:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-spellcheck-xh:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-spellcheck-zu:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice-pyuno:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice-xsltfilter:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice-graphicfilter:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice-ooofonts:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice-core01:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice-core02:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice-core03:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice-core04:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice-core05:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice-core06:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice-core07:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice.org-hunspell:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-hyphenation-en:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-hyphenation-fi:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-hyphenation-ga:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-hyphenation-hr:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-hyphenation-id:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-calc:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-writer:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-hyphenation-lt:
  Installed: (none)
  Candidate: 1.2.1-5
  Version table:
     1.2.1-5 500
        500 http://se.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://se.archive.ubuntu.com/ubuntu xenial/universe i386 Packages
openoffice.org-hyphenation-pl:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-hyphenation-ru:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice-en-us-writer:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice.org2-thesaurus:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-ure:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice-en-us-calc:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice-en-us-draw:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice.org-thesaurus-de:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice-calc:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice.org-thesaurus-it:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-thesaurus-pl:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-bundled:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice-impress:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice-en-us-math:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice-draw:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice-en-us:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice-en-us-impress:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice-math:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice.org-base:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-spellcheck-en-us:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-core:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice-unbundled:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-dev-doc:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice-en-us-base:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice.org-dmaths:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice-en-us-res:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice.org-spellcheck-de-at:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-spellcheck-de-ch:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-spellcheck-de-de:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice-base:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice-images:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice-javafilter:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 100
        100 /var/lib/dpkg/status
openoffice.org-unbundled:
  Installed: (none)
  Candidate: (none)
  Version table:
openoffice.org-hyphenation:
  Installed: 0.9
  Candidate: 0.9
  Version table:
 *** 0.9 500
        500 http://se.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://se.archive.ubuntu.com/ubuntu xenial/main i386 Packages
        100 /var/lib/dpkg/status
openoffice.org-thesaurus-en-au:
  Installed: (none)
  Candidate: (none)
  Version table:

```

---

### Post by mc4man on 2016-07-24
Just to check if any libreoffice packages are installed. This will either return nothing (none installed) or a number of entries, one for each installed package, the particulars don't matter - 
```
apt-cache policy libreoffice* |grep "Installed: 1:"
```
Post the results then *maybe* this can be fixed in short order

---

### Post by mc4man on 2016-07-24
With the performance of this forum going down, down, down I'll just post what I think you should try - 

Remove any libreoffice packages,
```
sudo apt purge libreoffice*
```
If that completes inc. the common package then remove all openoffice packages - 
```
sudo apt purge openoffice*
```
If that completes you should be able to install whatever libreoffice packages you want.
(or if on a recent Ubuntu Release install just install ubuntu-desktop to get the basic libreoffice packages installed

---

### Post by Karolina.K on 2016-07-24
this is the results, and yes the performance of the forums is very poor at the moment :( ```
 karolin@karolin-p6563sc:~$ apt-cache policy libreoffice* |grep "Installed: 1:"  Installed: 1:5.1.4-0ubuntu1
  Installed: 1:5.1.4-0ubuntu1
  Installed: 1:5.1.4-0ubuntu1
  Installed: 1:5.1.4-0ubuntu1
  Installed: 1:5.1.4-0ubuntu1
  Installed: 1:5.1.4-0ubuntu1
  Installed: 1:5.1.4-0ubuntu1
  Installed: 1:5.1.4-0ubuntu1
  Installed: 1:5.1.4-0ubuntu1
  Installed: 1:5.1.4-0ubuntu1
  Installed: 1:5.1.4-0ubuntu1
  Installed: 1:5.1.4-0ubuntu1
  Installed: 1:5.1.4-0ubuntu1
  Installed: 1:5.1.4-0ubuntu1
  Installed: 1:5.1.4-0ubuntu1
  Installed: 1:5.1.4-0ubuntu1
karolin@karolin-p6563sc:~$ 

```

---

### Post by smelheim85 on 2016-07-24
I don't think anyone has asked but have you already tried "apt-get autoremove" and what were the results?

---

### Post by mc4man on 2016-07-24
> **Karolina.K said:**
> this is the results, and yes the performance of the forums is very poor at the moment :( [code] karolin@karolin-p6563sc:~$ apt-cache policy libreoffice* |grep "Installed: 1:"  Installed: 1:5.1.4-0ubuntu1
  
Then go ahead & try the 2 purge commands _in order_, see what shakes loose..

---

### Post by Karolina.K on 2016-07-24
this is the result from the purge commands in order ```
 karolin@karolin-p6563sc:~$ sudo apt purge openoffice*

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'openoffice-ogltrans' for glob 'openoffice*'
Note, selecting 'openoffice-writer' for glob 'openoffice*'
Note, selecting 'openoffice.org-debian-menus' for glob 'openoffice*'
Note, selecting 'openoffice-gnome-integration' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-fr-fr' for glob 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-de-ch' for glob 'openoffice*'
Note, selecting 'openoffice-onlineupdate' for glob 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-en-ca' for glob 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-en-us' for glob 'openoffice*'
Note, selecting 'openoffice.org-updatedicts' for glob 'openoffice*'
Note, selecting 'openoffice-en-us-help' for glob 'openoffice*'
Note, selecting 'openoffice-ooolinguistic' for glob 'openoffice*'
Note, selecting 'openofficeorg-desktop-integration' for glob 'openoffice*'
Note, selecting 'openoffice.org-kde' for glob 'openoffice*'
Note, selecting 'openoffice.org-common' for glob 'openoffice*'
Note, selecting 'openoffice-ure' for glob 'openoffice*'
Note, selecting 'openoffice-desktop-integration' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-an' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-ca' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-eo' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-es' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-eu' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-fo' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-gl' for glob 'openoffice*'
Note, selecting 'openoffice-debian-menus' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-nb' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-nn' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-nr' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-ns' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-ss' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-st' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-tl' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-tn' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-uz' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-ve' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-xh' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-zu' for glob 'openoffice*'
Note, selecting 'openoffice-pyuno' for glob 'openoffice*'
Note, selecting 'openoffice-xsltfilter' for glob 'openoffice*'
Note, selecting 'openoffice-graphicfilter' for glob 'openoffice*'
Note, selecting 'openoffice-ooofonts' for glob 'openoffice*'
Note, selecting 'openoffice-core01' for glob 'openoffice*'
Note, selecting 'openoffice-core02' for glob 'openoffice*'
Note, selecting 'openoffice-core03' for glob 'openoffice*'
Note, selecting 'openoffice-core04' for glob 'openoffice*'
Note, selecting 'openoffice-core05' for glob 'openoffice*'
Note, selecting 'openoffice-core06' for glob 'openoffice*'
Note, selecting 'openoffice-core07' for glob 'openoffice*'
Note, selecting 'openoffice.org-hunspell' for glob 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-en' for glob 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-fi' for glob 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-ga' for glob 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-hr' for glob 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-id' for glob 'openoffice*'
Note, selecting 'openoffice.org-calc' for glob 'openoffice*'
Note, selecting 'openoffice.org-writer' for glob 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-lt' for glob 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-pl' for glob 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-ru' for glob 'openoffice*'
Note, selecting 'openoffice-en-us-writer' for glob 'openoffice*'
Note, selecting 'openoffice.org2-thesaurus' for glob 'openoffice*'
Note, selecting 'openoffice.org-ure' for glob 'openoffice*'
Note, selecting 'openoffice-en-us-calc' for glob 'openoffice*'
Note, selecting 'openoffice-en-us-draw' for glob 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-de' for glob 'openoffice*'
Note, selecting 'openoffice-calc' for glob 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-it' for glob 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-pl' for glob 'openoffice*'
Note, selecting 'openoffice.org-bundled' for glob 'openoffice*'
Note, selecting 'openoffice-impress' for glob 'openoffice*'
Note, selecting 'openoffice-en-us-math' for glob 'openoffice*'
Note, selecting 'openoffice-draw' for glob 'openoffice*'
Note, selecting 'openoffice-en-us' for glob 'openoffice*'
Note, selecting 'openoffice-en-us-impress' for glob 'openoffice*'
Note, selecting 'openoffice-math' for glob 'openoffice*'
Note, selecting 'openoffice.org-base' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-en-us' for glob 'openoffice*'
Note, selecting 'openoffice.org-core' for glob 'openoffice*'
Note, selecting 'openoffice-unbundled' for glob 'openoffice*'
Note, selecting 'openoffice.org-dev-doc' for glob 'openoffice*'
Note, selecting 'openoffice-en-us-base' for glob 'openoffice*'
Note, selecting 'openoffice.org-dmaths' for glob 'openoffice*'
Note, selecting 'openoffice-en-us-res' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-de-at' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-de-ch' for glob 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-de-de' for glob 'openoffice*'
Note, selecting 'openoffice.org' for glob 'openoffice*'
Note, selecting 'openoffice-base' for glob 'openoffice*'
Note, selecting 'openoffice-images' for glob 'openoffice*'
Note, selecting 'openoffice-javafilter' for glob 'openoffice*'
Note, selecting 'openoffice.org-unbundled' for glob 'openoffice*'
Note, selecting 'openoffice.org-hyphenation' for glob 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-en-au' for glob 'openoffice*'
Package 'openoffice.org-thesaurus-it' is not installed, so not removed
Note, selecting 'dictionaries-common' instead of 'openoffice.org-updatedicts'
Package 'openoffice.org-hunspell' is not installed, so not removed
Package 'openoffice.org-core' is not installed, so not removed
Note, selecting 'hunspell-an' instead of 'openoffice.org-spellcheck-an'
Package 'openoffice.org' is not installed, so not removed
Note, selecting 'hunspell-ca' instead of 'openoffice.org-spellcheck-ca'
Package 'openoffice.org-spellcheck-en-us' is not installed, so not removed
Note, selecting 'hunspell-eu' instead of 'openoffice.org-spellcheck-eu'
Note, selecting 'hunspell-gl-es' instead of 'openoffice.org-spellcheck-gl'
Note, selecting 'hunspell-uz' instead of 'openoffice.org-spellcheck-uz'
Package 'openoffice.org-writer' is not installed, so not removed
Note, selecting 'hyphen-en-us' instead of 'openoffice.org-hyphenation-en-us'
Note, selecting 'hyphen-en-us' instead of 'openoffice.org-hyphenation-en'
Package 'openoffice.org-hyphenation-hr' is not installed, so not removed
Note, selecting 'hyphen-pl' instead of 'openoffice.org-hyphenation-pl'
Note, selecting 'hyphen-ru' instead of 'openoffice.org-hyphenation-ru'
Package 'openoffice.org-base' is not installed, so not removed
Package 'openoffice-unbundled' is not installed, so not removed
Package 'openoffice.org-common' is not installed, so not removed
Package 'openoffice.org-dev-doc' is not installed, so not removed
Note, selecting 'myspell-eo' instead of 'openoffice.org-spellcheck-eo'
Note, selecting 'myspell-es' instead of 'openoffice.org-spellcheck-es'
Note, selecting 'myspell-fo' instead of 'openoffice.org-spellcheck-fo'
Note, selecting 'myspell-nb' instead of 'openoffice.org-spellcheck-nb'
Note, selecting 'myspell-nn' instead of 'openoffice.org-spellcheck-nn'
Note, selecting 'myspell-nr' instead of 'openoffice.org-spellcheck-nr'
Note, selecting 'myspell-ns' instead of 'openoffice.org-spellcheck-ns'
Note, selecting 'myspell-ss' instead of 'openoffice.org-spellcheck-ss'
Note, selecting 'myspell-st' instead of 'openoffice.org-spellcheck-st'
Note, selecting 'myspell-tn' instead of 'openoffice.org-spellcheck-tn'
Note, selecting 'myspell-ve' instead of 'openoffice.org-spellcheck-ve'
Note, selecting 'myspell-xh' instead of 'openoffice.org-spellcheck-xh'
Note, selecting 'myspell-zu' instead of 'openoffice.org-spellcheck-zu'
Note, selecting 'mythes-de' instead of 'openoffice.org-thesaurus-de'
Note, selecting 'mythes-de-ch' instead of 'openoffice.org-thesaurus-de-ch'
Note, selecting 'mythes-en-au' instead of 'openoffice.org-thesaurus-en-au'
Note, selecting 'mythes-en-au' instead of 'openoffice.org2-thesaurus'
Note, selecting 'mythes-pl' instead of 'openoffice.org-thesaurus-pl'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-en-ca'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-fi'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-ga'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-id'
Package 'openoffice.org-calc' is not installed, so not removed
Package 'openoffice.org-kde' is not installed, so not removed
Note, selecting 'myspell-fr-gut' instead of 'openoffice.org-spellcheck-fr-fr'
Note, selecting 'myspell-tl' instead of 'openoffice.org-spellcheck-tl'
Package 'openoffice.org-dmaths' is not installed, so not removed
Package 'openoffice.org-bundled' is not installed, so not removed
Package 'openoffice.org-ure' is not installed, so not removed
Note, selecting 'openoffice-debian-menus' instead of 'openoffice-desktop-integration'
Package 'openofficeorg-desktop-integration' is not installed, so not removed
Package 'openoffice.org-debian-menus' is not installed, so not removed
Package 'openoffice.org-hyphenation-lt' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:5.1.4) but it is not going to be installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-ja : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-sv : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-zh-tw : Depends: libreoffice-common but it is not going to be installed
 libreoffice-style-elementary : Depends: libreoffice-common (= 1:5.1.4-0ubuntu1) but it is not going to be installed
 libreoffice-style-galaxy : Depends: libreoffice-common (= 1:5.1.4-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
 
```

---

### Post by mc4man on 2016-07-24
You were to purge libreoffice first, then openoffice. Did you do that ? 
(- see nothing in what you just posted that indicates that.

---

