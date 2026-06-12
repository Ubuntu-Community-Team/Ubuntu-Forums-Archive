---
title: "Mistake in uninstalling"
date: 2008-03-28
forum: General Help
---

### Post by equal on 2008-03-28
So I installed Screenlets from a website, rather than using Synaptic. I downloaded the file, went into the folder, and entered

> sudo python setup.py install

It installed but then wouldn't work properly. Icouldn't figure out how to uninstall, and so like a n00b, I just deleted the ~/.screenlets folder.

now everytime i try to install or uninstall anything, it looks like this:

> phil@phil-desktop:~/screenlets$ sudo apt-get remove gnomebaker
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnomebaker
0 upgraded, 0 newly installed, 1 to remove and 42 not upgraded.
1 not fully installed or removed.
After this operation, 3039kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 110522 files and directories currently installed.)
Removing gnomebaker ...
Setting up screenlets (0.0.12-0ubuntu2) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing screenlets (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 screenlets
E: Sub-process /usr/bin/dpkg returned an error code (1)
phil@phil-desktop:~/screenlets$ 


Any clue how to make these errors go away?

---

### Post by equal on 2008-03-28
Nothing at all? If it helps, I installed it using a python installer script.

---

### Post by equal on 2008-03-28
yeah, I guess... going into the trash and UNdeleting the folder would have been the logical first step. HA! Everything works again :)

---

