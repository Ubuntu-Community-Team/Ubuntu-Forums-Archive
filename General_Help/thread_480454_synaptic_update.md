---
title: "synaptic update"
date: 2007-06-21
forum: General Help
---

### Post by unknownlaopoet on 2007-06-21
I had set up my proxy wrong earlier, but after changing proxy in pereferences it still sees the old proxy when i try to update

here is what i did



usr@usr:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
18% [Connecting to 16.101.160.111 (16.101.160.111)] [Connecting to 16.101.160.1
usr@usr:~$ sudo gedit /etc/apt/apt.conf
Password:
use@usr:~$
use@usr:~$

my apt.conf file shows which is the correct proxy

Acquire::http::Proxy "16.111.160.101";


is there another file that i should edit to fix this



Synaptic -> Settings -> Preferences -> Network, and select Manual Proxy Configuration

i also restarted the pc a couple of times after changing proxy to see if the settings were set.. which showed up after a few reboots so i did change it correctly

---

