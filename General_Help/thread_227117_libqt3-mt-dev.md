---
title: "libqt3-mt-dev"
date: 2006-08-01
forum: General Help
---

### Post by ozorba on 2006-08-01
I am trying to install libqt3-mt-dev and keep on getting the following errors:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libqt3-mt-dev: Depends: libqt3-mt (= 3:3.3.6-1ubuntu3) but 3:3.3.6-1ubuntu6 is to be installed
E: Broken packages


Further investigation showed that libqt3-mt is already installed. If I try to uninstall (so that I can re-install it again) it it tires to remove *all* the KDE components.

Has anyone got any ideas?

Thanx,
OZ

---

### Post by biovore on 2006-08-03
I have had this issue on to different machines.  It appears there is a package dependency conflict issue.  

The following packages have unmet dependencies:
  libqt3-mt-dev: Depends: libqt3-mt (= 3:3.3.6-1ubuntu3) but 3:3.3.6-1ubuntu6 is to be installed
E: Broken packages

I know there is a libqt3-mt-dev_3.3.6-1ubuntu6_i386.deb on the mirrors (or was) But it seems to have vanished, because apps seems to pull an old version of the libqt3-mt-dev packages and it looks for and old version of the libqt3-mt packages (which dosn't exist)

It may be that one of the us.archive.ubuntu.com mirrors isn't synced up right.

--------------------------
need the following in your repos (/etc/apt/sources.list)
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main multiverse restricted universe

then apt-get update
then apt-get upgrade
then apt-get install kdesdk

Worked here

---

