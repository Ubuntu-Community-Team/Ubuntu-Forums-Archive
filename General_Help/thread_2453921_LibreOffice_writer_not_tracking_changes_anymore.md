---
title: "LibreOffice writer not tracking changes anymore"
date: 2020-11-19
forum: General Help
---

### Post by wmrp on 2020-11-19
I proofread documents and have always used Track Changes, but as of today it is not  working anymore. It tracks nothing. Last night I installed some updates  of Ubuntu software (honestly, I didn't really check what exactly)  through Software Updater. Maybe there is a connection, but somehow I don't think so because when looking at LibreOfficeWriter under installed Ubuntu software it says it was never updated (but I may not understand what it refers to). Either way,  without Track Changes I cannot continue my work, so hopefully I can  receive help here. 
In Safe Mode it does not track changes either. 

Operating system: Ubuntu 20.04 
Libre Office writer version: 1:6.4.6-0ubuntu0.20.04.1

---

### Post by mastablasta on 2020-11-19
try with snap version and use a newer one. maybe it was resolved and patch hasn't made it back. i haven't seen any libre office updates in software updater in a while.

---

### Post by ActionParsnip on 2020-11-19
What is the output of:
```

apt-cache policy libreoffice

```
Thanks

---

### Post by wmrp on 2020-11-19
:~$ apt-cache policy libreoffice
libreoffice:
  Installed: (none)
  Candidate: 1:6.4.6-0ubuntu0.20.04.1
  Version table:
     1:6.4.6-0ubuntu0.20.04.1 500
        500 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 Packages
     1:6.4.2-0ubuntu3 500
        500 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) focal/universe amd64 Packages

---

### Post by wmrp on 2020-11-19
> **mastablasta said:**
> try with snap version and use a newer one. maybe it was resolved and patch hasn't made it back. i haven't seen any libre office updates in software updater in a while.

Sorry, I am new at this so not yet familiar with snap version. 

I may indeed uninstall and reinstall. I found this recommendation from LibreOffice support: 
**Complete Deinstallation**
 
[LIST]
[*]dpkg --list | awk '/ii/&&/libreoffice/{print $2}' | sudo xargs apt --yes purge
[*]sudo apt --yes autoremove
[*]sudo rm -r /usr/lib/libreoffice/* (ignore errors on this step)
[/LIST]
 **New Installation** (if using Ubuntu Base Repos or PPA)
 
[LIST]
[*]sudo apt update --yes
[*]sudo apt install libreoffice libreoffice-gtk3 libreoffice-sdbc-hsqldb libreoffice-help-en-us  --yes
[/LIST]

---

### Post by wmrp on 2020-11-19
> **wmrp said:**
> Sorry, I am new at this so not yet familiar with snap version. 

I may indeed uninstall and reinstall. I found this recommendation from LibreOffice support: 
**Complete Deinstallation**
 
[LIST]
[*]dpkg --list | awk '/ii/&&/libreoffice/{print $2}' | sudo xargs apt --yes purge 
[*]sudo apt --yes autoremove 
[*]sudo rm -r /usr/lib/libreoffice/* (ignore errors on this step) 
[/LIST]
 **New Installation** (if using Ubuntu Base Repos or PPA)
 
[LIST]
[*]sudo apt update --yes 
[*]sudo apt install libreoffice libreoffice-gtk3 libreoffice-sdbc-hsqldb libreoffice-help-en-us  --yes 
[/LIST]


Went through the above process, but behaves the same still; track changes does not work. So weird, as it used to work fine...

---

### Post by wmrp on 2020-12-09
> **mastablasta said:**
> try with snap version and use a newer one. maybe it was resolved and patch hasn't made it back. i haven't seen any libre office updates in software updater in a while.

How do I do that?

---

### Post by Hagar Delest on 2020-12-28
I doubt a new version would change anything.
Try to reset the profile. Close LO and  in ~/.config (hidden folder in your home), rename the libreoffice folder to "libreoffice old" (for example).
Then relaunch LO.
If it works fine again, then there was a problem with your profile. Either you continue with that brand new one or you can retrieve parts of the configuration by moving files from the old one to the new one.
If the track change still doesn't work, there is another problem.
Do you save in ODF (.odt)? If not, try to save in .odt.

---

