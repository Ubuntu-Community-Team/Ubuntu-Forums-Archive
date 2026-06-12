---
title: "New to Linux.. Installation problems"
date: 2007-10-14
forum: General Help
---

### Post by dmgthe2nd on 2007-10-14
Hey  everyone,

So I'm here trying to install Linux on my Dell Vostro 1500 Laptop.  I deleted all my partitions and everything related to windows.

When I boot the Ubuntu 7.04 from the CD drive, I see the menu and I click Start or Intall Ubuntu.
After that, I see the loading bar and it goes to a black screen saying:
"
BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)
"

I realize this might be popular problem but I have no knowledge when it comes to software-hardware relation issues.

All help is welcome!!
Thank you, David

---

### Post by r-mo on 2007-10-14
try pressing ctrl+alt+F8 while ubuntu is loading,  this should give you some diagnostic message as to where it's failing :(  It may also be worth trying gutsy when that's released in a few days or the alternative install cd

---

### Post by dmgthe2nd on 2007-10-14
Ctrl+alt+F8 didn<t work.   What's the alternative cd?

---

### Post by apunc1 on 2007-10-14
> The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installs on systems with less than about 256MB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably). 

[http://us.releases.ubuntu.com/7.04/](http://us.releases.ubuntu.com/7.04/)

scroll down about halfway to download the alternate cd version that matches your computer architecture.
this is Feisty.

---

