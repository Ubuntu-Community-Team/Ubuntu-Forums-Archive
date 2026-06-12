---
title: "Help With Installing Canon Printer/Scanner"
date: 2016-08-20
forum: General Help
---

### Post by gebecluck23 on 2016-08-20
Hello there, this is my first post on these forums, so I apologize if this is the wrong place to post...

Anyways, my trouble is that I'm having difficulty installing my (wireless) printer to my laptop. After searching the internet for quite a while, the best info I could find was here: [http://tipsonubuntu.com/2016/08/14/canon-printer-driver-scangear-mp-ubuntu-16-04/](http://tipsonubuntu.com/2016/08/14/canon-printer-driver-scangear-mp-ubuntu-16-04/)
I tried following the whole thing word for word, however Synaptic always gives me an error. Oddly enough, my printer actually seems to work somewhat with the current setup, (despite the error) but the scanner still doesn't work, and I don't really like the fact that there was any errors to begin with...

Here's as much relevant info as I can think of:
My Laptop is currently dual-booting Windows 10 and Ubuntu 16.04 LTS (64-bit system),
My printer is an American Canon MG5420 printer/copier/scanner,
And finally, the error itself happens whenever I hit "Apply" to start installing the driver packages, the error says:

"An error occured
 The following details are provided:
 E: /var/cache/apt/archives/cndrvcups-common-32_2.50-1-2~raring1_amd64.deb: trying to overwrite '/usr/lib/libc3pl.so.0', which is also in package cndrvcups-common:i386 2.50-1-2~raring1"

Any help at all would be appreciated, thanks in advance!

---

### Post by oldrocker99 on 2016-08-23
Try installing xsane, a GUI for sane, (scanner access made easy). It'll pull in the required dependencies. Is there a separate Canon scanner driver? Most all-in-ones have separate scanner drivers.

---

