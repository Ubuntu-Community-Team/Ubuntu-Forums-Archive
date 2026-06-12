---
title: "problem with update"
date: 2013-08-25
forum: General Help
---

### Post by melinda2 on 2013-08-25
Hi there, I am new in the forum, I have a problem with UPDATE MANAGER, and is shows me the message above

   'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

I have 12.04lts, I am waiting for your help. 
Thank you
Kind Regards
Melinda

---

### Post by plucky on 2013-08-25
> **melinda2 said:**
> Hi there, I am new in the forum, I have a problem with UPDATE MANAGER, and is shows me the message above

   'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

I have 12.04lts, I am waiting for your help. 
Thank you
Kind Regards
Melinda

Open a terminal and run ```
sudo rm -rf /var/lib/apt/lists/*
``` which will delete the .list files and then run ```
sudo apt-get update
``` to reload the .list files.

Good Luck & welcome to the forum.

---

