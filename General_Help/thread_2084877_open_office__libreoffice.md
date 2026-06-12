---
title: "open office / libreoffice"
date: 2012-11-16
forum: General Help
---

### Post by Synoc on 2012-11-16
using ubuntu 10.04/ tried installing libreoffice, 
 using these instructions
[http://www.ubuntugeek.com/install-libreoffice-in-ubuntu-11-0410-1010-04-using-ppa.html](http://www.ubuntugeek.com/install-libreoffice-in-ubuntu-11-0410-1010-04-using-ppa.html)

not only could I not install it because of broken dependencies, I could not install openoffice again after. 

what happened?
if I try to do an install 
```

sudo apt-get install openoffice.org
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openoffice.org: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.4) but it is not going to be installed
                  Depends: openoffice.org-writer but it is not going to be installed
                  Depends: openoffice.org-calc but it is not going to be installed
                  Depends: openoffice.org-impress but it is not going to be installed
                  Depends: openoffice.org-draw but it is not going to be installed
                  Depends: openoffice.org-math but it is not going to be installed
                  Depends: openoffice.org-base but it is not going to be installed
                  Depends: openoffice.org-report-builder-bin but it is not going to be installed
                  Depends: openoffice.org-officebean but it is not going to be installed
                  Recommends: openoffice.org-filter-binfilter but it is not going to be installed
E: Broken packages

```
that is what happens...
For the record Core is not installed because it says Common and ure  are not installed... I installed them myself manually, and it still says they are not installed. If I try to install core I still get
```

The following packages have unmet dependencies:
  openoffice.org-core: Depends: openoffice.org-common (> 1:3.2.0) but it is not going to be installed
                       Depends: ure (>= 1.6.0) but it is not going to be installed
E: Broken packages

```

---

### Post by apochry on 2012-11-16
Try this:

Remove LibreOffice and run:
```
sudo apt-get autoremove libreoffice-*
```Add Openoffice repository:
```
sudo add-apt-repository ppa:upubuntu-com/office
```Install OpenOffice:
```
sudo apt-get update
sudo apt-get install openoffice
```I hope that helps!

- Christo

---

### Post by Synoc on 2012-11-16
nope still broke same broke. openoffice isn't there and openoffice.org has broken packages

---

### Post by Synoc on 2012-11-16
gave up on OOo and just downloaded the deb files from LOo and did a manual install. it was a PITA but LLo works and always seemed to like me more. For anyone trying this on on 10.04. 

skip the automated method, 
purge openoffice*.* ```

sudo apt-get purge openoffice*.*

```
download the deb files from libreoffice.org/download, 

unpack them to a temp directory, navigate to that temp directory in terminal and type 
```

sudo dpkg -i *.deb

cd desktop-integration

sudo dpkg -i *.deb

```

then delete the temp directory altogether.

---

### Post by Hagar Delest on 2012-11-17
You can install AOO  and LibO with the .debs downloaded directly from the official web sites, This is the most robust method IMHO. Note that this way you can install and run both applications in parallel. But you need to remove the packages coming with the Ubuntu out of the box configuration first.

See: [[Ubuntu] Installing OOo on Debian and Co.](http://forum.openoffice.org/en/forum/viewtopic.php?f=74&t=68)

---

