---
title: "Ubuntu 12.10 Update Manager LP-PPA-libreoffice update broke package system"
date: 2013-03-25
forum: General Help
---

### Post by rechapman on 2013-03-25
An attempt to install the current LibreOffice update using the Update Manager resulted in a broken package system!!

> Details
> The following packages have unmet dependencies:
>
> libreoffice-core: Depends: libgcc1 (>- 1.4.1.1) but 1.4.6.3-1ubuntu5 is installed
> libreoffice-emailmerge

Now the Update Manager will NOT install updates including "Important security updates"!!! How is this problem fixed?

--

---

### Post by rechapman on 2013-03-25
Well I followed directions and it appears that

```
> sudo apt-get install -f
```
 'fixed' the broken package system.  LibreOffice seems to be updated and Update Manager reports that "The software on this computer is up to date".

I guess that "time will tell" if LibreOffice is working (as well as it can) and the system is NOT "hosed"! :o

[FWIW I really don't need this kind of drama -- I have real stuff that has to get done. :( ]

--

---

