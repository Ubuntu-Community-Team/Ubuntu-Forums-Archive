---
title: "How do you share a drive across a network?"
date: 2007-04-22
forum: General Help
---

### Post by Sir_Sid on 2007-04-22
Hi, I just installed ubuntu to use as a personal server for my files on my network. How do I share my drives across the network and make it accessible from my windows machines?

---

### Post by Jussi Kukkonen on 2007-04-22
You are looking for Samba: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

There are many ways to administer samba:
* edit the config files by hand (not that difficult)
* use Swat (a web based configurator): [https://help.ubuntu.com/community/Swat](https://help.ubuntu.com/community/Swat)
* use the KDE config in package kdenetwork-filesharing (you probably do not want this if you do not have kde libs installed)

---

