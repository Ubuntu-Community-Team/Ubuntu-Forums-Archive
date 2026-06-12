---
title: "setenv command. 14.04."
date: 2014-06-15
forum: General Help
---

### Post by zemega on 2014-06-15
I installed ncl from NCAR using the package ncl-ncarg using apt-get. There was a bug in the installation, I think, but it comes down to the ncl program has different structure of installation compared to Ubuntu/Debian. I filed a bug at the link below. For now, I found a work around it by just soft linking a folder from /usr/share to /usr/lib. I asked the developer, and they said:

'I think what's happening is that the installer is putting the  supplemental files in a non-standard location (for NCL), which is  /usr/share/ncarg, and hence in addition to NCARG_ROOT, you need to  setenv NCARG_NCARG to /usr/share/ncarg.'

There's no such package inside the repository. So, I'm quite confused to what should I do next. The program is actually in UNIX which are compatible in Linux (well, the binary installer works perferctly, its just the apt-get installation of ncl is wierd).

[https://bugs.launchpad.net/ubuntu/+source/ncl/+bug/1329691](https://bugs.launchpad.net/ubuntu/+source/ncl/+bug/1329691)

---

### Post by steeldriver on 2014-06-15
What are you asking exactly? setenv is a C-shell (csh/tcsh) built-in - if you are using bash the equivalent would be something like 'export NCARG_NCARG=/usr/share/ncarg', which you can add to your ~/.bashrc file if you want it to be available persistently

---

### Post by zemega on 2014-06-15
In other word, I should put this line 'export NCARG_NCARG=/usr/share/ncarg' inside /etc/environment for it to be accessible to all users. I started with Ubuntu 12.04, so all I know is anything related to Ubuntu usual including just the bash. So I don't really know about anything csh/tcsh. So this thread is considered closed. 

PS: You can say that I'm probably Ubuntu hardcore since I'm not interested in using any other distro.

---

