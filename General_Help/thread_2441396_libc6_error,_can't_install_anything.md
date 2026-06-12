---
title: "libc6 error, can't install anything"
date: 2020-04-23
forum: General Help
---

### Post by bertik23 on 2020-04-23
I wanted to install python-pip so i ran sudo apt install python-pip and got this error
  ```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libgcc1:i386 : Depends: libc6:i386 (>= 2.2.4) but it is not going to be installed
 libgcrypt20:i386 : Depends: libc6:i386 (>= 2.28) but it is not going to be installed
 libgpg-error0:i386 : Depends: libc6:i386 (>= 2.28) but it is not going to be installed
                      Recommends: libgpg-error-l10n:i386
 libidn2-0:i386 : Depends: libc6:i386 (>= 2.4) but it is not going to be installed
 liblz4-1:i386 : Depends: libc6:i386 (>= 2.4) but it is not going to be installed
 liblzma5:i386 : Depends: libc6:i386 (>= 2.17) but it is not going to be installed
 libunistring2:i386 : Depends: libc6:i386 (>= 2.7) but it is not going to be installed
 python-pip : Depends: python-pip-whl (= 18.1-5) but it is not going to be installed
              Recommends: python-all-dev (>= 2.6) but it is not going to be installed
              Recommends: python-setuptools but it is not going to be installed
              Recommends: python-wheel but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```it says Try "apt --fix-broken install" so I did that and got this
  ```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libc6:i386
Suggested packages:
  glibc-doc:i386 locales:i386
The following NEW packages will be installed:
  libc6:i386
0 upgraded, 1 newly installed, 0 to remove and 42 not upgraded.
88 not fully installed or removed.
Need to get 0 B/2578 kB of archives.
After this operation, 12.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 269716 files and directories currently installed.)
Preparing to unpack .../libc6_2.30-0ubuntu2.1_i386.deb ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing archive /var/cache/apt/archives/libc6_2.30-0ubuntu2.1_i386.deb (--unpack):
 new libc6:i386 package pre-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.30-0ubuntu2.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```  I tryied also running sudo apt-get install -f didn't work

  So what shall I do? Ubuntu 19.10

---

### Post by webaake on 2020-04-23
This is difficult to understand in your language. Could you please try to temporarily change it to english with the command LANG=C ? Like so;

LANG=C sudo apt-get install -f
or
LANGUAGE=en "command you want"

---

### Post by bertik23 on 2020-04-23
edited it to be english

---

### Post by CelticWarrior on 2020-04-23
What did you do before trying to install python-pip?

---

### Post by bertik23 on 2020-04-23
I tried to install a python package using pip, found out that pip is not installed and tried to install it

OR

few days ago I accidentaly cut the power while running firefox and than I got some error on boot, I fixed all the filles but as far as I can tell all were firefox related

---

### Post by mc4man on 2020-04-23
There are likely 3-4 files in /var/cache/debconf. You could mv them to a .bak or just delete them all. (I'd delete..
 Then sudo apt update and sudo apt install python-pip

---

### Post by bertik23 on 2020-04-23
that could be a problem

```

rm: remove write-protected regular file 'config.dat'? y
rm: cannot remove 'config.dat': Permission denied
rm: remove write-protected regular file 'config.dat-old'? y
rm: cannot remove 'config.dat-old': Permission denied
rm: remove write-protected regular empty file 'passwords.dat'? y
rm: cannot remove 'passwords.dat': Permission denied
rm: remove write-protected regular file 'templates.dat'? y
rm: cannot remove 'templates.dat': Permission denied
rm: remove write-protected regular file 'templates.dat-old'? y
rm: cannot remove 'templates.dat-old': Permission denied


```

---

### Post by bertik23 on 2020-04-23
ok I have done

sudo fuser -kv /var/cache/debconf/config.dat

and


 sudo apt --fix-broken install

and now it works

---

