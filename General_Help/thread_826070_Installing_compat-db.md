---
title: "Installing compat-db?"
date: 2008-06-11
forum: General Help
---

### Post by paulsjv on 2008-06-11
I am installing an old piece of software on my Ubuntu VM instance that the company I work for supports (it's an old version of ClearCase).  I seem to need libdb.so.3 but it's not availabe in my version of Ubuntu (8.04).  After doing some googling it pointed me to the direction of the CompatDB, which apparently has the libdb.so.3 file I need in the package.  I found the following web site: [http://compatdb.majorgeeks.com/](http://compatdb.majorgeeks.com/) which tells you how to get the compatdb package for Ubuntu by editing the /etc/sources.list and adding a mirror.  However, this doesn't seem to work for me as I get the following error.  Anyone have any suggestions as to either get the compatdb or libdb.so.3 on my file system so I can install the software I need to install?  Thanks!

$ sudo apt-get install compatdb.org-linux
[sudo] password for jpaulson:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package compatdb.org-linux


> Debian/Ubuntu Users
CompatDB.org is available over apt-get. Here is the apt repository for /etc/apt/sources.list:

# CompatDB.org
deb [http://MIRROR/apt/](http://MIRROR/apt/) ./

You need to replace MIRROR with the actual mirror. For example: deb [http://compatdb.majorgeeks.com/apt/](http://compatdb.majorgeeks.com/apt/) ./

The following packages are available over apt:
compatdb.org-windows
compatdb.org-linux
compatdb.org-macos

The compatibility data will be installed in the /usr/share/compatdb.org-<database> directory.

---

### Post by paulsjv on 2008-06-12
*bump*

---

### Post by prshah on 2008-06-12
> **paulsjv said:**
> how to get the compatdb package for Ubuntu by editing the /etc/sources.list and adding a mirror.


After changing the sources list, you have to give```
sudo apt-get update
``` to ensure that the new sources information is integrated into the available software database.

If you get an error with the above command, you've probably made a mistake in adding the mirror line to your sources.list. In that case, please post your sources.list file here.

---

### Post by paulsjv on 2008-06-12
AH!  That is a nice to know. :)  Thanks for the hint!

---

