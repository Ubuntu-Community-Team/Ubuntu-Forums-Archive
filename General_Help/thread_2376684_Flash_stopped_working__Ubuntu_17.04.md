---
title: "Flash stopped working / Ubuntu 17.04"
date: 2017-11-04
forum: General Help
---

### Post by Dennola4 on 2017-11-04
I'm on an Acer Aspire 5750. 

OS: Ubuntu 17.04
Release:	17.04
Codename: zesty

EDIT: I uninstalled all things flash, reinstalled flashplayer-installer and restarted. Flash is now working properly in Firefox but not in Chromium. I prefer Chromium, as it is a bit faster, so any help would be awesome. Thanks.

EDIT: I have already tried this, as recent posts suggest....

> dennis@dennis-Aspire-5750:~$ sudo apt install adobe-flashplugin
[sudo] password for dennis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'adobe-flashplugin' has no installation candidate


---

### Post by Dennis N on 2017-11-04
What version of Chromium Browser? If newest version, 62, then you need to enter URL of any site where you want flash to work in Settings > advanced > content settings > flash.

---

### Post by again? on 2017-11-04
> **Dennola4 said:**
> dennis@dennis-Aspire-5750:~$ sudo apt install adobe-flashplugin
[sudo] password for dennis: 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'adobe-flashplugin' has no installation candidate

You need to enable the partner repository for the 'adobe-flashplugin' package to be available.
[https://help.ubuntu.com/stable/ubuntu-help/addremove-sources.html#canonical-partner](https://help.ubuntu.com/stable/ubuntu-help/addremove-sources.html#canonical-partner)

---

### Post by Dennola4 on 2017-11-05
SOLVED. 

Thanks guys. I did what **guber2** suggested and enabled the partner repo under the "other software tab". Once the repo was updated I was able to install adobe-flashplugin. Interestingly, none of the sites that test to see if flash is installed recognized the plug-in until I took **Dennis N**'s suggestion. They recognized the plug-in only after I added the website in Chromium settings> advanced> privacy_&_security> content_settings> flash and then restarted the browser. 

Sheesh. Oh well.... rumor is flash will be obsolete by 2020.

---

