---
title: "System error after installing Skype ubuntu 14.10"
date: 2015-01-25
forum: General Help
---

### Post by klaudyna on 2015-01-25
Hi,

recently I've installed Ubuntu 14.10 on my hard disk on Samsung N145 Plus Mini-Laptop (or netbook,or whatever it's called). I have exp with Mint and Ubuntu 10.04. 
Ubuntu 14.10 is a bit slower than debian versions but I wanted to try it (to learn why people don't like it). It's quite cool and everything works fine for me (even the graphic card, though there was always a lot of problems with Samsung N145+ with Linux cause the graphic drivers are not supported for Linux...bloody Samsung!). But today I've installed Skype (from official Skype website,for Ubuntu 12,because it was the only avalaible version on their website).I can use Skype,camera works well,maybe there is a bit issue with desktop view share but all the other things works very well. But...Yeah
1) computer started to get REALLY slow,even when Skype is off
2) there is a system error every time I restart my laptop (the error appears just after the system is turned on)

Anyone knows that problem? Any clue what is it about?


ERROR DETAILS:

Internal system error

ExecutablePath /lib/systemd/systemd-logind
Package systemd 208-8ubuntu8.2
ProblemType Crash
Title systemd-logind crashed with SIGABRT
ApportVersion 2.14.7-0ubuntu8.1
Architecture i386
Distro Ubuntu 14.10
InstallationMedia Ubuntu 14.10 "Utopic Unicorn" - Release i386 (20141022.1)
PackageArchitecture i386
ProcCmdline /lib/systemd/systemd-logind

---

### Post by Jonathan Precise on 2015-01-25
> **klaudyna said:**
> Hi,

recently I've installed Ubuntu 14.10 on my hard disk on Samsung N145 Plus Mini-Laptop (or netbook,or whatever it's called). I have exp with Mint and Ubuntu 10.04. 
Ubuntu 14.10 is a bit slower than debian versions but I wanted to try it (to learn why people don't like it). It's quite cool and everything works fine for me (even the graphic card, though there was always a lot of problems with Samsung N145+ with Linux cause the graphic drivers are not supported for Linux...bloody Samsung!). But today I've installed Skype (from official Skype website,for Ubuntu 12,because it was the only avalaible version on their website).I can use Skype,camera works well,maybe there is a bit issue with desktop view share but all the other things works very well. But...Yeah
1) computer started to get REALLY slow,even when Skype is off
2) there is a system error every time I restart my laptop (the error appears just after the system is turned on)

Anyone knows that problem? Any clue what is it about?


ERROR DETAILS:

Internal system error

ExecutablePath /lib/systemd/systemd-logind
Package systemd 208-8ubuntu8.2
ProblemType Crash
Title systemd-logind crashed with SIGABRT
ApportVersion 2.14.7-0ubuntu8.1
Architecture i386
Distro Ubuntu 14.10
InstallationMedia Ubuntu 14.10 "Utopic Unicorn" - Release i386 (20141022.1)
PackageArchitecture i386
ProcCmdline /lib/systemd/systemd-logind

Hello klaudyna, welcome to the forums.

It would be helpful to post the specs, so we can see what's going on, and recommend a lighter flavor of Ubuntu, like Xubuntu, Lubuntu or Ubuntu MATE (that last one is still unofficial, but it's damn good If you want 10.04-ish look and feel and speed).

1) See the ups, maybe vanilla Ubuntu is just too heavy for you, maybe installing Gnome Flashback and choosing the "No effects" version at login. Maybe trying Ubuntu MATE 14.04 LTS. I recommend it over 14.10, because it's an LTS and it has support for 5 years. Stability is a plus on LTS, unless you run into issues (like I did, hence I have 14.10).

2) Sorry, not familiar with logind issues, so can't help you here. Wait until someone that can, or try LTS to see if it works.

---

