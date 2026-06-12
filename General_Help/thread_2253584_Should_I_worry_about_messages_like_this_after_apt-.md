---
title: "Should I worry about messages like this after apt-get update?"
date: 2014-11-20
forum: General Help
---

### Post by chris322 on 2014-11-20
W: GPG error: [https://download.01.org](https://download.01.org) trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A902DDA375E52366
W: Duplicate sources.list entry [http://ppa.launchpad.net/colingille/freshlight/ubuntu/](http://ppa.launchpad.net/colingille/freshlight/ubuntu/) saucy/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_colingille_freshlight_ubuntu_dists_saucy_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/colingille/freshlight/ubuntu/](http://ppa.launchpad.net/colingille/freshlight/ubuntu/) saucy/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_colingille_freshlight_ubuntu_dists_saucy_main_binary-i386_Packages)

---

### Post by plucky on 2014-11-21
> W: GPG error: [https://download.01.org](https://download.01.org) trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A902DDA375E52366

Open a terminal and run ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A902DDA375E52366
``` should fix the GPG error.

> W: Duplicate sources.list entry [http://ppa.launchpad.net/colingille/freshlight/ubuntu/](http://ppa.launchpad.net/colingille/freshlight/ubuntu/) saucy/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_colingille_freshlight_ubuntu_dis ts_saucy_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/colingille/freshlight/ubuntu/](http://ppa.launchpad.net/colingille/freshlight/ubuntu/) saucy/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_colingille_freshlight_ubuntu_dis ts_saucy_main_binary-i386_Packages) 


Are you running 13.10 or 14.04?

If 14.04 you should delete those entries in **Software Sources** as there are no Trusty Repositories for that PPA.

Good Luck

---

