---
title: "Feisty Server Hangs on apt-get update"
date: 2007-09-07
forum: General Help
---

### Post by pcuff on 2007-09-07
When I run apt-get update on my Feisty server it hangs when getting the multiverse packages.


Get:1 http://ubuntu.cs.utah.edu feisty Release.gpg [191B]
Ign http://ubuntu.cs.utah.edu feisty/main Translation-en_US
Ign http://ubuntu.cs.utah.edu feisty/restricted Translation-en_US
Ign http://ubuntu.cs.utah.edu feisty/multiverse Translation-en_US
Ign http://ubuntu.cs.utah.edu feisty/universe Translation-en_US
Get:2 http://ubuntu.cs.utah.edu feisty-updates Release.gpg [191B]
Ign http://ubuntu.cs.utah.edu feisty-updates/main Translation-en_US
Ign http://ubuntu.cs.utah.edu feisty-updates/restricted Translation-en_US
Ign http://ubuntu.cs.utah.edu feisty-updates/multiverse Translation-en_US
Ign http://ubuntu.cs.utah.edu feisty-updates/universe Translation-en_US
Get:3 http://ubuntu.cs.utah.edu feisty-security Release.gpg [191B]
Ign http://ubuntu.cs.utah.edu feisty-security/main Translation-en_US
Ign http://ubuntu.cs.utah.edu feisty-security/restricted Translation-en_US
Ign http://ubuntu.cs.utah.edu feisty-security/multiverse Translation-en_US
Ign http://ubuntu.cs.utah.edu feisty-security/universe Translation-en_US
Get:4 http://ubuntu.cs.utah.edu feisty-backports Release.gpg [191B]
Ign http://ubuntu.cs.utah.edu feisty-backports/main Translation-en_US
Ign http://ubuntu.cs.utah.edu feisty-backports/restricted Translation-en_US
Ign http://ubuntu.cs.utah.edu feisty-backports/multiverse Translation-en_US
Ign http://ubuntu.cs.utah.edu feisty-backports/universe Translation-en_US
Get:5 http://ubuntu.cs.utah.edu feisty Release [57.2kB]
Get:6 http://ubuntu.cs.utah.edu feisty-updates Release [32.4kB]
Get:7 http://ubuntu.cs.utah.edu feisty-security Release [50.9kB]
Get:8 http://ubuntu.cs.utah.edu feisty-backports Release [44.6kB]
Get:9 http://ubuntu.cs.utah.edu feisty/main Packages [1007kB]
Get:10 http://ubuntu.cs.utah.edu feisty/restricted Packages [7628B]
Get:11 http://ubuntu.cs.utah.edu feisty/multiverse Packages [148kB]
90% [9 Packages bzip2 0] [11 Packages 25678/148kB 17%]Timeout, server not responding.


The only think I know of to do is physically restart the system when this happens, so I avoid apt-get update, especially since I ssh into the system, so I'm not physically near it when this happens, and it absolutely stops responding.

I've seen others with this same problem, but I've never seen a good resolution.  In fact, I thought changing mirrors would solve the problem.  Before I was just using the ubuntu servers in sources.list.  Today I decided to change to a mirror (as the pasted text indicates), but it still froze.

---

