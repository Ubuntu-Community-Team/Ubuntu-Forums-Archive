---
title: "&quot;Run as a different user&quot; broken?"
date: 2007-05-09
forum: General Help
---

### Post by Myrgen on 2007-05-09
After upgrading to Feisty Fawn, I noticed that the command 'Run as a different user', found in Applications -> System Tools, gives an error message: Failed to execute child process "gksuexec" (No such file or directory)

Anyone has an idea how to fix this?
Thank you in advance.
Myrgen

---

### Post by baka_rob on 2007-05-11
Did something happen to the gksu package?  Maybe it got uninstalled and "Run as a different user" wasn't removed from the menu (or maybe it wasn't installed by default for some reason)?

What happens if you run "apt-get install gksu" as root (or use your favourite package manager)?

Or maybe gksuexec isn't in PATH anymore?  But you may want to check that package, first.

---

### Post by Myrgen on 2007-05-11
> **baka_rob said:**
> Did something happen to the gksu package?  Maybe it got uninstalled and "Run as a different user" wasn't removed from the menu (or maybe it wasn't installed by default for some reason)?

What happens if you run "apt-get install gksu" as root (or use your favourite package manager)?

Or maybe gksuexec isn't in PATH anymore?  But you may want to check that package, first.

This is what I get when running apt-get install gksu:

root@aurora:/home/myriam# apt-get install gksu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gksu is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

As to check gksuexec, I'm sorry but I must confess that I'm rather new at this, and I have no idea how to do that.. :(

Thank you for helping me, though.. :)

---

