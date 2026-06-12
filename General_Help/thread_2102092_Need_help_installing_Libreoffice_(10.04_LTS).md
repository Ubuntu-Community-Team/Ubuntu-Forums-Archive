---
title: "Need help installing Libreoffice (10.04 LTS)"
date: 2013-01-06
forum: General Help
---

### Post by WeAreLinux on 2013-01-06
Good Morning

I'm trying to install libreoffice via these instructions --> [https://wiki.ubuntu.com/LibreOffice](https://wiki.ubuntu.com/LibreOffice)

After entering the full install command, I get this:

>  Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libreoffice: Depends: libreoffice-core (= 1:3.5.4-0ubuntu1~lucid1) but it is not going to be installed
               Depends: libreoffice-writer but it is not going to be installed
               Depends: libreoffice-calc but it is not going to be installed
               Depends: libreoffice-impress but it is not going to be installed
               Depends: libreoffice-draw but it is not going to be installed
               Depends: libreoffice-math but it is not going to be installed
               Depends: libreoffice-base but it is not going to be installed
               Depends: libreoffice-filter-mobiledev but it is not going to be installed
               Depends: libreoffice-java-common (>= 1:3.5.4~) but it is not going to be installed
               Recommends: libreoffice-gnome but it is not going to be installed or
                           libreoffice-kde but it is not going to be installed
E: Broken packages


How can I fix this? I'm using Ubuntu 10.04 LTS & would like to install libreoffice since openoffice isn't supported anymore. I really only need the word processor.

Before trying this, I uninstalled openoffice via Ubuntu Software Center. 

Thanks

---

### Post by iMurshaq on 2013-01-06
might sound stupid but have you actually tried to install libreoffice from the software center

---

### Post by iMurshaq on 2013-01-06
have you entered these commands

sudo add-apt-repository ppa:libreoffice/ppa 

sudo apt-get update

---

