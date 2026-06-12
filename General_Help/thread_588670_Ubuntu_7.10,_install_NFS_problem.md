---
title: "Ubuntu 7.10, install NFS problem"
date: 2007-10-23
forum: General Help
---

### Post by Agnus on 2007-10-23
Hello I am trying to install NFS according the instructions of this page: [HOWTO: NFS Server/Client]("http://ubuntuforums.org/showthread.php?t=249889")

I type:
sudo apt-get install nfs-kernel-server nfs-common portmap

and I get:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package nfs-kernel-server

---

### Post by prince_niceguy on 2007-10-23
can you search in synaptic if the same are present..

if not enable the repository universe, multiverse from the settings --> repositories in synaptic.

now click reload and these should come up.

---

### Post by prince_niceguy on 2007-10-23
another easier way is to click system --> administration --> shared folder  from the top menu. It will by itself install the required softwares.

---

