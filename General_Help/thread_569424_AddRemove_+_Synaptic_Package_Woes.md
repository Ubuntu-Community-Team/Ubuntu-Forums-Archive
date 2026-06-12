---
title: "Add/Remove + Synaptic Package Woes"
date: 2007-10-07
forum: General Help
---

### Post by mr_mann14 on 2007-10-07
Absolutely new to linux in general, but fairly tech savy.  Now I have a problem with both my add/remove and Synaptic Package Manger.  It believe it started while I was following some guides on google to set up my Intel 4965AGN wireless which seems to now be running alright under ndiswrapper. I get the following errors with add/remove:
> 
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f

And when I run Synaptic I get:
> An error occured

The following details are provided:
[QUOTE]E: Dynamic MMap ran out of room
E: Error occurred while processing openoffice.org-calc (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
[/QUOTE]

I've tried the whole sudo apt-get install/upgrade/update but I seem to get an error with each of them. Any help would be greatly appreciated!

---

### Post by Celegorm on 2007-10-07
Post the contents of '/etc/apt/sources.list' As the add/remove errors suggest, the problem may be something in that file that is not correct.

---

### Post by mr_mann14 on 2007-10-07
Yeah, stupid me, my bad.  I forgot to remove a couple lines from the sources.list from when i was trying to install wireless. Thanks though.

---

