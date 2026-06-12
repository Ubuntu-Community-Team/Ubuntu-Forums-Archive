---
title: "Help needed on vmware-tools installation"
date: 2006-11-15
forum: General Help
---

### Post by ATIR350 on 2006-11-15
I'm running a fresh installation of Ubuntu 6.06 on VMWare Workstation 5.5.1 build-19175
This is wt I did to install VMWare-tools:

-Install build-essential
-Install linux-headers for my kernel
-extracted the vmware tar.gz file to my home folder
-in terminal, did a sudo ./vmware-install.pl
-left installation directories by default:
  binary files installed to                     /usr/bin
  directory that contains the init directories(rc0.d to rc6.d)                   
                                                /etc
  directory that contains the init scripts      /etc/init.d

The following error occurs:
-Unable to copy the source file ./installer/services.sh to the   destination file /etc/init.d/vmware-tools. Execution aborted.

What should be done to fix that?
Thx!

---

