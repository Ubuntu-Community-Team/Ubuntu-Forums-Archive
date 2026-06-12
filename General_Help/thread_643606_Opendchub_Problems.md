---
title: "Opendchub Problems"
date: 2007-12-18
forum: General Help
---

### Post by duffmckagan on 2007-12-18
I have installed Kubuntu Gutsy Gibbon 7.10 on my system. 

Opendchub doesn't take the new settings I make when I edit the .config file present in .opendchub (in my home folder)
The version it says I am running when I type opendchub -h is version 0.7.14
But apt-get has a different opinion.
This is what I get if I do aptitude show opendchub. 

> Package: opendchub
State: installed
Automatically installed: yes
**Version: 0.7.15-1**
Priority: optional
Section: universe/net
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 315k
Depends: libc6 (>= 2.5-5), libcap1, libperl5.8 (>= 5.8.8)
Description: hub clone for DC (Direct Connect P2P network)
 Open DC hub is a Unix/Linux version of the hub software for the Direct Connect network.  Direct Connect is a file sharing network made up
 by hubs, to which clients can connect.  It offers offers peer-based file-sharing. In practise it works better than gnutella and other
 similar systems as it allows dc hubs (servers) administrators to require clients to share specified amount of data.  The amount is usually
 based on type of client's connection and it is used not to hurt or exclude anybody but to make file sharing "fair play".

 This version supports most of the features of the official hub. Some of the currently supported features are:
 * Searching for files,
 * Connecting to users, both in active and passive mode,
 * Messaging in open chat,
 * Private messaging,
 * Registering users,
 * Kicking users (for OP:s),
 * Banning users (for Admins),
 * Uploading hub address and description to public hub list,
 * Hublinking, which makes it possible to search on other hubs connected to the network.

 The hub is run as a daemon, i.e, it runs in the background.  It's administrated through a tcp connection, for example with telnet, which
 makes it possible to administer remotely, given that the user has the administration password.

 Homepage: [http://opendchub.sourceforge.net](http://opendchub.sourceforge.net)



---

### Post by duffmckagan on 2007-12-29
Reported Bug 179160 [https://bugs.launchpad.net/ubuntu/+source/opendchub/+bug/179160](https://bugs.launchpad.net/ubuntu/+source/opendchub/+bug/179160)

...after I got a li'l impatient [;)]

---

