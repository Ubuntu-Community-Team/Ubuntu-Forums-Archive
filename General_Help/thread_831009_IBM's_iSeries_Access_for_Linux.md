---
title: "IBM's iSeries Access for Linux"
date: 2008-06-16
forum: General Help
---

### Post by btc2008 on 2008-06-16
Does anybody have any experience with:

[COLOR="Blue"]Linux requirements for running iSeries Access for Linux

GLibc 2.2 
RPM 3.0 
OpenMotif 2.0 or later for the 5250 emulator 
unixODBC driver manager version 2.0.11 or later must be installed on the client. Go to the unixODBC Project web site for more information on the driver manager and to download the latest level of the driver manager. 
Recommended iSeries LPAR (Power PC) Linux Distributions: 

Suse Linux Enterprise Server 8 and later 
Red Hat Enterprise Linux 3 and later 

Note: if you recompile the unixODBC driver manager, the ./configure --prefix default is /usr/local. If you use this default, you may need to update your shared library (/etc/ld.so.conf) and executable paths to include it.[/COLOR]


I am new to Ubuntu and am enjoying it very much. For work, I need to access our AS400 though IBM's iSeries Access.

Does anybody know if this program will run under Ubuntu?

Thanks

Bruce

---

