---
title: "FAQ: What is the command string for updating packages?"
date: 2004-11-04
forum: General Help
---

### Post by Adam Boettiger on 2004-11-04
I'm coming from Fedora side of things. What command line strings should be issued to update currently installed packages on a regular basis?

Is there a setting in Ubuntu that can check for package updates on a recurring basis automatically and prompt me to install the updates?

AB

---

### Post by Rancoras on 2004-11-04
Please post requests for support in the appropriate forum.  The only things that should be posted here are *answers* to FAQs and *step by step* HOWTOs.  Mod, please move this to General Support.

---

### Post by fng on 2004-11-04
First you need to update the sources list:
$> apt-get update

With the next command, you can install upgrades for allready installed packages
$> apt-get upgrade

Because of the release policy of ubuntu, only security fixes will be upgraded.  You will hardly find any new version of the packages.  They will be saved for the next ubuntu release.

Finally, when a new ubuntu release is out, you can switch to it with this command: 
$> apt-get dist-upgrade

---

