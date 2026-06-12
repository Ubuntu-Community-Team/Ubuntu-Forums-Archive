---
title: "AWN applets not showing up even after successful install"
date: 2008-04-16
forum: General Help
---

### Post by ddado on 2008-04-16
Okay, here's my problem: I've installed AWN 0.3.1 and AWN Manager from trunk... Now, i wanted to do the same with the AWN applets so i downloaded them from [https://launchpad.net/~awn-testing/+archive](https://launchpad.net/~awn-testing/+archive) and installed it through the AWN Manager, but they still don't show up (not even after rebooting).

so i tried to install them directly from the repositories through the terminal, but here's what i got:

> dado@dado:~$ sudo apt-get install awn-extras-applets-trunk
[sudo] password for dado:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package awn-extras-applets-trunk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package awn-extras-applets-trunk has no installation candidate
dado@dado:~$ 


Now, i really don't know what to do! AWN is working just fine, it's only the applets that i'm missing. Anybody got any suggestions?
Thanx in advance!

P.S: I'm running Gutsy (64bit version). Plus, in the attachment below, you will see the list of my repositories... whereas the two starting with "download.tuxfamily.org " aren't reachable for some reason...

---

