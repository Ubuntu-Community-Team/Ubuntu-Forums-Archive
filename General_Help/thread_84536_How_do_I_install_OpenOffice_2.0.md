---
title: "How do I install OpenOffice 2.0?"
date: 2005-10-31
forum: General Help
---

### Post by blueturtl on 2005-10-31
Looked over the forums, only repository links usually have to do with Breezy. The OpenOffice in the Hoary backports is still a beta. I then went to openoffice.org and downloaded the install file. "RPMs! Oh no!" I thought to myself, and then stumbled upon Alien, which supposedly converts RPMs to DEB packages. The conversion went smoothly, but after installation none of the newly added menu items did anything. Tried locating the executable by hand and it looks like a 'sh' file instead of a binary.

Does anyone know of a repository with an up-to-date version of OO for Hoary?
Does anyone know how to successfully install OO2?

I want the new Office for the OpenDocument format.

---

### Post by blueturtl on 2005-10-31
Ok, if not can someone running 1.1.3 at least post me their /etc/openoffice/autoresponse.conf file? Apparently my attempted OO2 install screwed up the old OpenOffice.

---

### Post by simplyw00x on 2005-11-01
[ENVIRONMENT]
INSTALLATIONMODE=INSTALL_WORKSTATION
INSTALLATIONTYPE=WORKSTATION
UPDATEMODE=IF_AVAILABLE
DESTINATIONPATH=<home>/.openoffice/1.1.3
OUTERPATH=
LOGFILE=

[JAVA]
JavaSupport=none

---

### Post by blueturtl on 2005-11-17
Oh come now? I thought the time of upgrading your OS to get the latest apps would be over with Linux :???: 

I know Ubuntu is fairly new, so to expect Ubuntu packages on the OpenOffice.org site is a bit much, but heck they only have RPMS! Can it be compiled in source, or is everyone OO2 really upgrading to Breezy?

---

### Post by blueturtl on 2005-11-17
Got it fixed, here's a howto on the subject in case someone else has the same problem:
[http://ubuntuforums.org/showthread.php?t=91624](http://ubuntuforums.org/showthread.php?t=91624)

---

