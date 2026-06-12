---
title: "Installing libreoffice 3.6"
date: 2012-12-14
forum: General Help
---

### Post by mahela007 on 2012-12-14
I'm trying to install the latest version of libreoffice on my Ubuntu PC. (running Ubuntu 10.04)
I've added the following PPA 
[http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu)

However, 
when I try sudo apt-get install libreoffice I get the following error: 
```
Reading package lists... Done
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

```

When I first tried to install the new libreoffice, it somehow deleted the current installation of libreoffice. That may have resulted in the broken packages. 
sudo apt-get install -f doesn't seem to work.

---

### Post by Rexilion on 2012-12-14
Got some bad news it seems. I went to [it's site]("https://launchpad.net/~libreoffice") and looked for the [packages for lucid]("https://launchpad.net/~libreoffice/+archive/ppa?field.series_filter=lucid"). These went up till version 3.5.6. Further digging revealed that [it's build failed]("https://launchpadlibrarian.net/114237874/buildlog_ubuntu-lucid-i386.libreoffice_1%3A3.5.6-0ubuntu1~lucid1_FAILEDTOBUILD.txt.gz"). Yet it was noted as 'delivered', a PPA expert might explain that. Makes no sense to me...

---

### Post by sahabcse on 2012-12-14
Try the following

sudo add-apt-repository ppa:libreoffice/ppa 
sudo apt-get update
sudo apt-get install libreoffice-gnome

---

