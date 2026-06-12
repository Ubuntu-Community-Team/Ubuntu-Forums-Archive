---
title: "question about disk utility in ubuntu 13.04"
date: 2013-10-13
forum: General Help
---

### Post by hunterkasy on 2013-10-13
I am wondering how accurate the disk utility is when you use the smart tool, to check the status of the hhd?

I have a 3 month old ssd drive that disk utility smart says it has 149 bad sectors just trying to figure out if that is right or a false positive

---

### Post by Dennis N on 2013-10-13
I believe the values are stored with the hard drive itself, so it is as good as the disk's own data. You can also retrieve the results and other information about the disk from:

**sudo smartctl --all /dev/sda** (if disk is sda)

Note: The package **smartmontools** must be installed to use this command.

More information here:

[http://sourceforge.net/apps/trac/smartmontools/wiki](http://sourceforge.net/apps/trac/smartmontools/wiki)

---

