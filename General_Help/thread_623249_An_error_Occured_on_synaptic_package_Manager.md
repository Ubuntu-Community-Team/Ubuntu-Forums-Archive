---
title: "An error Occured on synaptic package Manager"
date: 2007-11-25
forum: General Help
---

### Post by mojoaw on 2007-11-25
hiya for all i am new on Ubuntu  and let me tell you all i rely like Ubuntu  a Lot  but for some reason i got some problems installing package's getting the following error 

E: axyl-lucene: subprocess post-installation script returned error exit status 2

system info: 
Ubuntu 7.10 (gusty)
Kernel 2.20.1
GNOME 2.20.1
Memory   3.2gb
Processor Intel(R) core(TM)2 CPU  660@ 2.40
Processor Intel(R) core(TM)2 CPU  660@ 2.40


System Status:  
Available disk Space : 203.GB



thanks on advance
:)

---

### Post by apetresc on 2007-11-25
That is strange; can you try typing, at a prompt,```
sudo apt-get install axyl-lucene
```The error should occur here too, and it will probably give more details. Please paste **all** the output of that command here, and we'll see what the problem is :)

---

### Post by mojoaw on 2007-11-25
Reading package lists... Done
Building dependency tree       
Reading state information... Done
axyl-lucene is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up axyl-lucene (2.1.9) ...
/usr/share/axyl/lucene/install/install-lucene.sh: 59: Syntax error: "(" unexpected
dpkg: error processing axyl-lucene (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 axyl-lucene
E: Sub-process /usr/bin/dpkg returned an error code (1)


 thanks AdrianP

---

### Post by apetresc on 2007-11-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/axyl-lucene/+bug/157505](https://bugs.launchpad.net/ubuntu/+source/axyl-lucene/+bug/157505) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Ah, I see; that's a configuration bug for that specific package; I was able to find a Launchpad bug in reference to this: [https://bugs.launchpad.net/ubuntu/+source/axyl-lucene/+bug/157505](https://bugs.launchpad.net/ubuntu/+source/axyl-lucene/+bug/157505)

You should subscribe to this bug in Launchpad and track its progress; there's nothing I (or anyone on this forum) can help with, it'll be up to the package maintainer for axyl-lucene to fix this. Sorry :(

---

### Post by mojoaw on 2007-11-25
thanks  and will subscribe :)

---

