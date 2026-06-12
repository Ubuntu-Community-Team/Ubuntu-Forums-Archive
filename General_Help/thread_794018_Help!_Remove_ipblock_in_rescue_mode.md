---
title: "Help! Remove ipblock in rescue mode?"
date: 2008-05-14
forum: General Help
---

### Post by masht on 2008-05-14
I have a remote server managed by ssh. I installed ipblock, which is causing big troubles. No connections possible anymore. I can only boot into rescue mode now. 

I tried removing with "aptitude purge iplist" witch gave me following:


Reading Package Lists... Done
Building Dependency Tree
Initializing package states... Done
Reading task descriptions... Done
Couldn't find any package matching "iplist".  However, the following
packages contain "iplist" in their description:
  libjudy-dev libjudydebian1
W: Warning: could not lock the cache file.  Opening in read-only mode
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
Reading Package Lists... Done
Building Dependency Tree
Initializing package states... Done
Reading task descriptions... Done
W: Warning: could not lock the cache file.  Opening in read-only mode


Anybody has an answer? How could I stop ipblock from loading up at startup?

Thanks for any help in advance, masht.

---

### Post by uljanow on 2008-05-15
Autostart can be disabled by changing the value of AUTOSTART in /etc/ipblock.conf to "no".

---

