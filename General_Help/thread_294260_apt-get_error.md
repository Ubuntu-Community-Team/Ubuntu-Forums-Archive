---
title: "apt-get error"
date: 2006-11-06
forum: General Help
---

### Post by kitchens on 2006-11-06
I've searched the forum but I haven't found anyone w/ this exact issue. Sorry in advance if it's been addressed before.
On my edgy machine I get this error when trying to apt-get:
```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up and (1.2.2-1.1) ...
Starting auto nice daemon: invoke-rc.d: initscript and, action "start" failed.
dpkg: error processing and (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 and
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Has anyone else seen this problem?
Thanks

---

### Post by taurus on 2006-11-06
Can I ask why you have to run that command, "sudo apt-get -f install"?  What happens if you run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by kitchens on 2006-11-06
update returns no error.
upgrade returns this:
```
sudo aptitude update
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
Writing extended state information... Done
Get:1 http://www.getautomatix.com edgy Release.gpg [189B]
Ign http://www.getautomatix.com edgy/main Translation-en_US
Hit http://www.getautomatix.com edgy Release
Hit http://www.getautomatix.com edgy/main Packages
Get:2 http://archive.ubuntu.com edgy Release.gpg [191B]
Ign http://archive.ubuntu.com edgy/main Translation-en_US
Get:3 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Ign http://archive.canonical.com dapper-commercial/main Translation-en_US
Get:4 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Ign http://archive.ubuntu.com edgy/universe Translation-en_US
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US
Ign http://archive.ubuntu.com edgy/restricted Translation-en_US
Get:5 http://archive.ubuntu.com edgy-proposed Release.gpg [191B]
Ign http://archive.ubuntu.com edgy-proposed/main Translation-en_US
Ign http://archive.ubuntu.com edgy-proposed/universe Translation-en_US
Hit http://archive.canonical.com dapper-commercial Release
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Hit http://security.ubuntu.com edgy-security Release
Ign http://archive.ubuntu.com edgy-proposed/multiverse Translation-en_US
Ign http://archive.ubuntu.com edgy-proposed/restricted Translation-en_US
Get:6 http://archive.ubuntu.com edgy-updates Release.gpg [189B]
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_US
Hit http://archive.canonical.com dapper-commercial/main Packages
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_US
Hit http://security.ubuntu.com edgy-security/main Packages
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_US
Get:7 http://archive.ubuntu.com edgy-backports Release.gpg [189B]
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US
Hit http://security.ubuntu.com edgy-security/universe Packages
Hit http://security.ubuntu.com edgy-security/multiverse Packages
Hit http://security.ubuntu.com edgy-security/restricted Packages
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US
Get:8 http://archive.ubuntu.com edgy-security Release.gpg [191B]
Ign http://archive.ubuntu.com edgy-security/main Translation-en_US
Hit http://archive.ubuntu.com edgy Release
Hit http://archive.ubuntu.com edgy-proposed Release
Hit http://archive.ubuntu.com edgy-updates Release
Hit http://archive.ubuntu.com edgy-backports Release
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/universe Sources
Hit http://security.ubuntu.com edgy-security/multiverse Sources
Hit http://security.ubuntu.com edgy-security/restricted Sources
Hit http://archive.ubuntu.com edgy-security Release
Hit http://archive.ubuntu.com edgy/main Packages
Hit http://archive.ubuntu.com edgy/universe Packages
Hit http://archive.ubuntu.com edgy/multiverse Packages
Hit http://archive.ubuntu.com edgy/restricted Packages
Hit http://archive.ubuntu.com edgy/main Sources
Hit http://archive.ubuntu.com edgy/universe Sources
Hit http://archive.ubuntu.com edgy/multiverse Sources
Hit http://archive.ubuntu.com edgy/restricted Sources
Hit http://archive.ubuntu.com edgy-proposed/main Packages
Hit http://archive.ubuntu.com edgy-proposed/universe Packages
Hit http://archive.ubuntu.com edgy-proposed/multiverse Packages
Hit http://archive.ubuntu.com edgy-proposed/restricted Packages
Hit http://archive.ubuntu.com edgy-proposed/main Sources
Hit http://archive.ubuntu.com edgy-proposed/universe Sources
Hit http://archive.ubuntu.com edgy-proposed/multiverse Sources
Hit http://archive.ubuntu.com edgy-proposed/restricted Sources
Hit http://archive.ubuntu.com edgy-updates/main Packages
Hit http://archive.ubuntu.com edgy-updates/universe Packages
Hit http://archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://archive.ubuntu.com edgy-updates/restricted Packages
Hit http://archive.ubuntu.com edgy-updates/main Sources
Hit http://archive.ubuntu.com edgy-updates/universe Sources
Hit http://archive.ubuntu.com edgy-updates/multiverse Sources
Hit http://archive.ubuntu.com edgy-updates/restricted Sources
Hit http://archive.ubuntu.com edgy-backports/main Packages
Hit http://archive.ubuntu.com edgy-backports/universe Packages
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages
Hit http://archive.ubuntu.com edgy-backports/restricted Packages
Hit http://archive.ubuntu.com edgy-backports/main Sources
Hit http://archive.ubuntu.com edgy-backports/universe Sources
Hit http://archive.ubuntu.com edgy-backports/multiverse Sources
Hit http://archive.ubuntu.com edgy-backports/restricted Sources
Hit http://archive.ubuntu.com edgy-security/main Packages
Hit http://archive.ubuntu.com edgy-security/main Sources
Fetched 8B in 2s (4B/s)
Reading package lists... Done
jkitchens@amd64:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  mozilla-firefox-locale-en-gb
The following packages have been kept back:
  libggi2 mplayer proftpd python-gadfly python-htmltmpl python-kjbuckets
  python-osd python-soappy python-syck
0 packages upgraded, 0 newly installed, 1 to remove and 9 not upgraded.
Need to get 0B of archives. After unpacking 758kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 126862 files and directories currently installed.)
Removing mozilla-firefox-locale-en-gb ...
Setting up and (1.2.2-1.1) ...
Starting auto nice daemon: invoke-rc.d: initscript and, action "start" failed.
dpkg: error processing and (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 and
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up and (1.2.2-1.1) ...
Starting auto nice daemon: invoke-rc.d: initscript and, action "start" failed.
dpkg: error processing and (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 and

```

---

### Post by rpkehoe on 2006-11-06
Have you recently installed a new package that has not worked correctly?  I had a similar situation where I had to reinstall the package that was not working correctly, then remove it.  After that all was well.

---

### Post by NeoLithium on 2006-11-06
> 
The following packages are unused and will be REMOVED:
  mozilla-firefox-locale-en-gb

It looks as if apt doesn't want to remove this package quite yet.  Try this order, hopefully it will work:
```

sudo apt-get remove mozilla-firefox-locale-en-gb

sudo apt-get update

sudo apt-get upgrade

```

---

### Post by kitchens on 2006-11-06
I've tried to apt-get remove the package but I get the same error that I get with a apt-get -f install

---

