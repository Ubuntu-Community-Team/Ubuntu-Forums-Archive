---
title: "simple scan and xsane not able to connect with my canon mg4120 printer"
date: 2016-11-30
forum: General Help
---

### Post by juntjoo2 on 2016-11-30
So I tried to install the drivers from here: [http://tipsonubuntu.com/2016/08/14/canon-printer-driver-scangear-mp-ubuntu-16-04/](http://tipsonubuntu.com/2016/08/14/canon-printer-driver-scangear-mp-ubuntu-16-04/)

but when I try to install one file which turns out to be two after synaptic manager finds it I get this error:

E: /var/cache/apt/archives/cndrvcups-common-32_2.50-1-2~raring1_amd64.deb: trying to overwrite '/usr/lib/libc3pl.so.0', which is also in package cndrvcups-common:i386 2.50-1-2~raring1

So one of them installs, but only the i386 one installs.  The two other files from the link above installed successfully.  I don't know if this is why simple scan and xsane aren't connecting to my printer but hopefully someone does.

I already tried reinstalling both simple scan and xsane, rebooted, same issue. If it matters any I can print fine, just no scan.


...


found this command in another thread: 

ben@Hal:~$ scanimage -L
device `pixma:MG4100_10.0.0.6' is a CANON Canon PIXMA MG4100 multi-function peripheral

---

