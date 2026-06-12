---
title: "Problems with Update Manager / Synaptic"
date: 2008-03-14
forum: General Help
---

### Post by dylanologist on 2008-03-14
I'm having a problem updating my Ubuntu 7.10 (64 bit) desktop.  When I click on the updates are available notification I get:

Not all updates can be installed.
Run a partial upgrade to install as many updates as possible.

I'm presented with the options: Partial Upgrade or Close



If I select Partial Upgrade I get:

Unable to get an exclusive lock.
This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.



If I select Close and then select Install Updates I get:

An error occurred.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



I get the same message when I try to run Synaptic (though I did not try to run both applications at the same time).



In a terminal, <sudo dpkg --configure -a> gives me:

Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1



I'm still somewhat on the noobish side, and this stuff is definitely over my head.  Any ideas what the problem might be and how to go about fixing it?

---

### Post by {BzF}~JOKesTER on 2008-03-14
Ok I Whould Be Very Carefull About This And Maybe Backup Your Data To A Flash Drive Or External.

I've Been Helping Several Poeple With The Exact Same Problem - It May Be A Bug In An Update>?

To Be Updated Please View This Link.

[http://ubuntuforums.org/showthread.php?t=724273:](http://ubuntuforums.org/showthread.php?t=724273:))

---

### Post by dylanologist on 2008-03-14
Thanks, I'll follow that thread, as it does seem to be my problem exactly.

---

### Post by SerafeimG on 2008-04-21
Yeah, that's it!
I had exactly the same problem. I solved it by following the instructions of the tread given above and specially be copying and past a file given from utUtu in post numbered #47.
I still get the "Partial Upgrade" message when I start Update Manager. If you try to partial upgrade, the update manager closes and does absolutely nothing.
Dynalogist, what about you? Have you fixed this minor problem?

---

