---
title: "Linux-Image Server upgrade?"
date: 2012-12-28
forum: General Help
---

### Post by isac630728 on 2012-12-28
Hi All,

When I try to install snmpd services, I get a error message as below.

The following packages have unmet dependencies:
 linux-image-server : Depends: linux-image-3.2.0-34-generic but it is not going                                                                                                                                                               to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s                                                                                                                                                              olution).

I want to know if I type apt-get -f install, will it bring down any services or the server? Does it need a reboot after updating? I'm working on a production server and I don't want to mess up.

Server version 3.2.0-32-generic 

Server:~$sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-23-generic linux-headers-3.2.0-31-generic linux-headers-3.2.0-26-generic linux-headers-3.2.0-23 linux-headers-3.2.0-25 linux-headers-3.2.0-31 linux-headers-3.2.0-26 linux-headers-3.2.0-32 linux-headers-3.2.0-27
  linux-headers-3.2.0-33 linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic linux-headers-3.2.0-32-generic linux-headers-3.2.0-27-generic linux-headers-3.2.0-25-generic linux-headers-3.2.0-33-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.2.0-35-generic linux-image-server linux-server
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
[B]The following NEW packages will be installed:
  linux-image-3.2.0-35-generic
The following packages will be upgraded:
  linux-image-server linux-server[/B]
2 upgraded, 1 newly installed, 0 to remove and 84 not upgraded.
8 not fully installed or removed.
Need to get 38.5 MB of archives.
After this operation, 149 MB of additional disk space will be used.
Do you want to continue [Y/n]?

Should I continue? I wont continue unless someone is sure that it wont  bring down the server or any services..

---

