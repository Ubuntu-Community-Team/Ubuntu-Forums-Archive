---
title: "Firefox 3 Install on Fiesty Fawn"
date: 2008-06-19
forum: General Help
---

### Post by measekite on 2008-06-19
My OS is Feisty Fawn 7.04.  Synaptic only has Firefox 2 installed.  I cannot find any deb files.  I downloaded a tar file from Moxilla.

What are the cookbook steps so I can install Firefox 3 over my current Firefox 2?

---

### Post by russlar on 2008-06-19
> **measekite said:**
> My OS is Feisty Fawn 7.04.  Synaptic only has Firefox 2 installed.  I cannot find any deb files.  I downloaded a tar file from Moxilla.

What are the cookbook steps so I can install Firefox 3 over my current Firefox 2?

If you got the tar from mozilla, run tar -xvfj *name_of_file*. this will create a firefox directory with all the firefox 3.0 files inside them. move this directory to somewhere like /opt or /usr/etc and run the file called firefox. create launchers where-ever you want them.

---

### Post by aysiu on 2008-06-19
Try this:
[http://www.psychocats.net/ubuntu/firefox#terminal](http://www.psychocats.net/ubuntu/firefox#terminal)

---

### Post by russlar on 2008-06-19
> **aysiu said:**
> Try this:
[http://www.psychocats.net/ubuntu/firefox#terminal](http://www.psychocats.net/ubuntu/firefox#terminal)

useful. \\:D/

---

### Post by measekite on 2008-06-19
> **aysiu said:**
> Try this:
[http://www.psychocats.net/ubuntu/firefox#terminal](http://www.psychocats.net/ubuntu/firefox#terminal)

Do not get me wrong but I thought Ubuntu would maintain earlier releases like 7.04 and 7.10 for 18 months.  I assumed that the package system would also be ubdated with the latest release like Firefox3 and later versions of Thunderbird.

It is a real pain in the butt to have to maintain many items that are not in the package system.

The two good things about Wiindows (I do like Ubuntu and no longer use Windows much) is that the hardware mfg (printers, cameras etc) support Windows as they do Mac and to install a Windows program you just down load the application and run setup.exe and everything is done for you.

Somehow the powers to be in Linux need to recognize why Linux will always lag behind Windows until this is done.

---

### Post by russlar on 2008-06-19
> **measekite said:**
> Somehow the powers to be in Linux need to recognize why Linux will always lag behind Windows until this is done.

The thing with community-based linux, like ubuntu, is that you are the powers that be.

---

### Post by aysiu on 2008-06-19
> **measekite said:**
> Do not get me wrong but I thought Ubuntu would maintain earlier releases like 7.04 and 7.10 for 18 months.  I assumed that the package system would also be ubdated with the latest release like Firefox3 and later versions of Thunderbird.

It is a real pain in the butt to have to maintain many items that are not in the package system. No. The Ubuntu policy is to just provide security updates. Once a version of Ubuntu is released, no new software versions will be released for it. So you have the options of sticking with old software (that still gets security updates), updating Ubuntu every six months to get new software, or using tricky workarounds to get new software on an older release.

Perhaps a rolling release distro might suit your better? Debian testing or Arch, perhaps? This little bit came along with the latest release of Linux Mint, which is based on Ubuntu: > Although Linux Mint isn't a rolling distribution an LTS strategy will be put in place to ensure that Linux Mint 5 Elyssa will stay up to date over the next 2 years. Users will have the choice to enable the backport repository for Elyssa in which upgrades for important desktop applications (Firefox, Thunderbird, OpenOffice..) will be made available.

> The two good things about Wiindows (I do like Ubuntu and no longer use Windows much) is that the hardware mfg (printers, cameras etc) support Windows as they do Mac and to install a Windows program you just down load the application and run setup.exe and everything is done for you.

Somehow the powers to be in Linux need to recognize why Linux will always lag behind Windows until this is done. I see. So Linux needs to recognize that hardware manufacturers support Windows? I think they already recognize that.

Personally I prefer a software package manager. I'm tired of searching for .exe and .dmg files.

---

### Post by itisbasi on 2008-10-14
> **aysiu said:**
> Try this:
[http://www.psychocats.net/ubuntu/firefox#terminal](http://www.psychocats.net/ubuntu/firefox#terminal)

Very good guide..

---

