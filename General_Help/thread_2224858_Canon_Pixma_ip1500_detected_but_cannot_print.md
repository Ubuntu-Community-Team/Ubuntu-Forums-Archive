---
title: "Canon Pixma ip1500 detected but cannot print"
date: 2014-05-18
forum: General Help
---

### Post by deamon_knight on 2014-05-18
Just as it says in the title. I have a canon Pixma ip1500 printer. This printer works normally in Windows, but using the printer configuration panel in Lubuntu, I can add it as a printer and I can select to print to this device, but nothing prints out.

I'm running Lubuntu 14.04 LTS x64.

---

### Post by dragonfly41 on 2014-05-18
This might help you .. [http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html](http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html)

check printer again after these instructions are followed.

---

### Post by deamon_knight on 2014-05-23
I can add that PPA , but when I update the sources I get

```
W: Failed to fetch http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Not sure how to proceed. Thanks.

---

### Post by dragonfly41 on 2014-05-23
It seems that trusty is not on distribution list ...

[http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/)

I have drivers installed on Ubuntu 12.04 for ip2600 series

Go to Ubuntu Software Centre and search cnijfilter ..

I don't see cnijfilter-ip1500series in the repo list
so you could try installing the next release up .. 

such as 

cnijfilter-common .... needed as common
and
cnijfilter-ip1800series ... match your printer

---

### Post by marksmarks on 2014-05-27
I don't use the Lubuntu version, so am not sure of your exact configuration.  (I do use Ubuntu Trusty 14.04 however)

It seems to me that the Trusty Canon drivers (filters) are in the Gruz, --> -trunk <--, PPA.   Not the 'regular' Gruz PPA.

I'm on my Ubuntu 14.04 box as I type this, and the Gruz  (trunk) PPA driver **cnijfilter-ip1500series** is listed in Synaptic.


Would my previous posts help any??

see: [http://ubuntuforums.org/showthread.php?t=2220935&highlight=](http://ubuntuforums.org/showthread.php?t=2220935&highlight=)

-----------------
...

Add the gruz PPA (Click on &#8220;Technical details about this PPA&#8221; and select your OS version), then update Synaptic, ...

For Ubuntu 12.04, 12.10, 13.04, 13.10, 14.04; [https://launchpad.net/~michael-gruz/+archive/canon-trunk](https://launchpad.net/~michael-gruz/+archive/canon-trunk)

NEXT...
...
----------------------

---

### Post by deamon_knight on 2014-05-28
Marksmarks, I removed the regular Gruz PPA and added the trunk PPA. It looks like there is a cnijfilter-common-32 and cnijfilter-common-64 package and a cnijfilter-pixmaip1500series-32 package (no cnijfilter-pixmaip1500series-64 I think). I tried installing cnijfilter-common-64 and cnijfilter-pixmaip1500series-32, and I can install a printer through the "Configure Printer" application, and add my printer as described in the post you linked. However, when I select to print a test page or any other document, it seems to complete when looking at the print queue, but there is no actual output from my printer.

I tried removing cnijfilter-common-64 and adding cnijfilter-common-32 instead and I have the same problem. 

Nothing seemed to indicated that it depended on the libtiff4 library, but I tried to install that but it did not solve the problem.

---

