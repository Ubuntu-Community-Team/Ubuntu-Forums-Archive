---
title: "Error Message when opening Synaptic"
date: 2008-04-03
forum: General Help
---

### Post by Nifty Nate on 2008-04-03
I just tried opening Synaptic and this error message popped up.


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by HereInOz on 2008-04-03
This means that you need to open a terminal - Alt-F3 - and enter the command:

sudo dpkg --configure -a

You will then be asked for your password - the one you use to log on.  Enter you password and the command should run and hopefully it will fix the problem.

If it does, you will be smiling, if it doesn't, hopefully someone here can assist you.

---

### Post by Nifty Nate on 2008-04-03
Worked like a charm. Thanks.

---

### Post by kushykush on 2008-04-03
I am getting the following error:  How to correct????

GPG error: [http://ftp.debian.org](http://ftp.debian.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg)  
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/i18n/Translation-en_US.bz2](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/i18n/Translation-en_US.bz2) 
:confused:

---

