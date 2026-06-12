---
title: "ZFS RAM usage (not using enough!)"
date: 2016-11-10
forum: General Help
---

### Post by firefoxx04 on 2016-11-10
Hello,

I have been using ZFS for some time now. I have recently moved the server to a vmware host and given it 4gb of ram (it used to have 8gb).

I am not using dedup or any other ram intensive features of ZFS.

When I ran a scrub before, the system used 6-7GB of the 8GB of ram. With 4GB of ram, the system is only using 2gb (50%). ZFS will not use more ram even though it has access to it. The server is only hosting files and can afford to give ZFS more ram. 

It is also worth noting that my 1GB swap is not being used either. 

Is their a configuration somewhere that tells ZFS to use more ram? I think I read that somewhere but cannot seem to find anything on that. I would love for it to use 3GB (75%), otherwise I am going to just give it 2GB of ram (which it runs completely fine with!)


And before anyone says I need more ram, my system is on a gigabit network and my pool is more than capable of saturating that link without any sort of caching function. I am well aware of ZFS RAM requirements for specific features (such as compression and duplication). 


Thank you for any help!

---

### Post by kingneutron on 2016-12-02
--These may help:
REFS:
[http://www.solaris-cookbook.eu/linux/linux-ubuntu/debian-ubuntu-centos-zfs-on-linux-zfs-limit-arc-cache/](http://www.solaris-cookbook.eu/linux/linux-ubuntu/debian-ubuntu-centos-zfs-on-linux-zfs-limit-arc-cache/)
[https://bbs.archlinux.org/viewtopic.php?id=171559](https://bbs.archlinux.org/viewtopic.php?id=171559)

--Honestly, since the system only has 4GB I wouldn't worry about it unless it's seriously impacting I/O speed. The OS still needs some free RAM to cache and run things. (Don't forget cron jobs like updatedb.)  As long as it's not using excessive swap and running OK, I'd say no need to worry.

---

