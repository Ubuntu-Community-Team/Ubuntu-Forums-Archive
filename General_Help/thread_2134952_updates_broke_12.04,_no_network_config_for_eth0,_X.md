---
title: "updates broke 12.04, no network config for eth0, X won't load during boot."
date: 2013-04-12
forum: General Help
---

### Post by pksings on 2013-04-12
Nothing else changed, just installed updates. 

What a mess,still trying to find out why X won't load. I manually re-created a working /etc/networking/interfaces file and got eth0 up. Network Manager has a "version" problem and is non-functional.  

this is very bad folks....

I hope I'm alone, if not this will really cause a stink....

Some progress, Nvidia module is loaded but not working. Init 1, rmmod nvidia, depmod -a, modprobe nvidia, init 2 , the GUI come up and I can login. Searching for why.....

Mostly solved, still have to unload nvidia and reload it or no X. Going to init 1 and back to init 2 without unloading it locks up the machine......

A little progress, downgrading network-manager fixed it's problems, so now my network settings and configuration are back to normal.

X on the other hand.... Nvidia fails to find screens during initial load, but rmmod, insmod of same module fixes it and then it works fine. Upgraded driver from nvidia-current to newest and it made no difference.  Still stumped.   Working though, but requires removing module and re-inserting it, then init 1, and init 2, to get there.

---

