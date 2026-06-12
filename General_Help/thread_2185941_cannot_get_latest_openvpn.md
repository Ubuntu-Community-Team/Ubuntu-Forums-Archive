---
title: "cannot get latest openvpn"
date: 2013-11-05
forum: General Help
---

### Post by jj4 on 2013-11-05
The version of openvpn on my client is
openvpn --version
OpenVPN 2.2.1 i686-linux-gnu [SSL] [LZO2]

However, no matter what repo I add, it will not update to the latest version.
ANy ideas which repo I am supposed to be using and how to add it?

---

### Post by claracc on 2013-11-05
As I can see from the openvn repository in launchpad: [https://launchpad.net/ubuntu/+source/openvpn](https://launchpad.net/ubuntu/+source/openvpn) the release for ubuntu precise pangolin is 2.2.1, which is what you have. (I am suppossing your ubuntu is 12.04)

I suppose that in order to have the last released package 2.2.3 you will need to compile the source code for creating the bin software. The process is described here: [http://openvpn.net/index.php/open-source/documentation/install.html?start=1](http://openvpn.net/index.php/open-source/documentation/install.html?start=1).

Other possibility is to upgrade your ubuntu to the lastest saucy salamnder wich has a repository for the openvn version you want, but I think it is like killing flies with a cannon.

---

