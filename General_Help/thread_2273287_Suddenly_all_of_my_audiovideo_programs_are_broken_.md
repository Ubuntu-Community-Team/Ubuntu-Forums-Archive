---
title: "Suddenly all of my audio/video programs are broken and can't be re-installed"
date: 2015-04-11
forum: General Help
---

### Post by matt174 on 2015-04-11
I tried installing a few new codecs for videos, but the downloads failed. Subsequently, audacity and audacious were uninstalled (but not gmusicbrowser), along with all video playing software. I try to reinstall, but this is what I get:

```
matias@matias-Aspire-E3-111:~$ sudo apt-get install audacious
[sudo] password for matias: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 audacious : Depends: audacious-plugins (>= 3.4.3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

Using synaptic or the software center doesn't rememdy things either.

Please help!

---

### Post by dino99 on 2015-04-12
start by purging your 'newly' installed codecs (you can get that list by glancing at the synaptic history (left pane))
then reinstall the ubuntu-desktop meta-package (if you were using it, otherwise select the appropriate one)

from a terminal you can also:
- update the archive (but close synaptic first): sudo apt-get update
- try to fix the missing package(s): sudo apt-get install -f
- reconfigure: sudo dpkg --configure -a

---

