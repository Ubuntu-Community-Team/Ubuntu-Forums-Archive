---
title: "Trying to install Librewolf"
date: 2024-07-06
forum: General Help
---

### Post by billywyatt2 on 2024-07-06
I've been trying to download and install Librewolf but have so far failed. I thought i had downloaded the repositories but when i tried to install Librewolf with ```
sudo apt install librewolf
``` it failed?
So i tried to find Librewolf via the terminal and that failed as well. I then opened up the Synaptic Package Manager and did a search there but all i got was:

Could not download all repository indexes
The repository 'https://deb.librewolf.net Noble Release' does not have a Release file.

Could someone help please.

---

### Post by Holger_Gehrke on 2024-07-06
From [https://librewolf.net/installation/debian/:](https://librewolf.net/installation/debian/:)
> 
**Attention.** We only build LibreWolf for Debian 11/12, Ubuntu 20/21/22 and Mint 20.2/20.3/21.

So the repository you're trying to download from has no packages for Noble (yet). If you set up the repo the way they describe it on that page, it will try to install the build for Ubuntu 20.04 (focal) on your system, which may or may not work.

Holger

---

### Post by ActionParsnip on 2024-07-06
[https://librewolf.net/installation/debian/](https://librewolf.net/installation/debian/)

Clearly stated on the librewolf website.

---

### Post by currentshaft on 2024-07-06
I can't believe people trust Firefox derivatives like this.

I spent about 15 minutes trying to find out who builds Librewolf, how, on what infrastructure, etc. Nothing in the official documentation.

Zero information about the individuals responsible for this product in the License and Privacy Policy documents.

Even assuming these mysterious developers are all highly skilled, benevolent and able to withstand MICE, this thing is always going to be behind published, WELL KNOWN Firefox vulnerabilities, yet even automatic updates have been disabled. They even disable Safe Browsing, for crying out loud, so known sites spreading malware and zero-days are all available.

What a recipe for failure and actual security risk.

---

