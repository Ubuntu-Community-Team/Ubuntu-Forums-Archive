---
title: "C Header files location"
date: 2007-06-19
forum: General Help
---

### Post by nhnewbie on 2007-06-19
While running the VMwareTools Installer its requesting the location of the C Header files. The default location given /usr/src/linux/include does not work.  What files could I search for that would give me the location?  

:)

---

### Post by longlegs on 2007-06-21
Hi ,
It may be that the header files are not there!  Use synaptic pkg manager to install them (look for something like libc???? or header), then VMWare can find them.

Good luck
longlegs

---

### Post by mawdryn on 2007-06-21
You need to make sure that the packages linux-headers-2.6.xx-xx are installed and I think also the build-essentials package. The location you would then specify would be along the lines of /usr/src/linux-headers-2.6.xx-xx/linux/include (replace the x's with your kernel subversion)

---

### Post by Bachstelze on 2007-06-21
A nice shortcut to automatically install the headers for your current running kernel :

```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by nhnewbie on 2007-06-26
I know this reply took a long time in coming but the sudo apt-get .... command helped.  
Thank you all for your help.  

A grateful newbie!

---

