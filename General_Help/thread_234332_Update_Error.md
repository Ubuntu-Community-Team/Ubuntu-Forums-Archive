---
title: "Update Error"
date: 2006-08-11
forum: General Help
---

### Post by mikesena on 2006-08-11
This should be easy to fix, but I'm not sure how.

I get this error when updating:```
http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release: Unable to find expected entry  multivers/binary-i386/Packages in Meta-index file (malformed Release file?)
```I have done an aptitude update.  My sources.list file contains:```
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -
# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://hk.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://hk.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

deb http://wine.budgetdedicated.com/apt dapper main
deb http://hk.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multivers
```Anyone know what's wrong?

---

### Post by rjl6591 on 2006-08-11
The 'e' is missing from the last 'multiverse' in your sources.list

---

