---
title: "Default kernel settings throttle Filezilla FTP"
date: 2016-05-24
forum: General Help
---

### Post by faster7on7windows on 2016-05-24
The default sysctl settings limit Filezilla transfers to 800KB/s per thread. Applying this modification removes the limit:
```
sysctl -w net.ipv4.tcp_rmem='40960 873800 62914560'
sysctl -w net.core.rmem_max=8388608
```

Do distros ever modify the Linux kernel? If so is there any chance Ubuntu apply these settings by default so Filezilla works properly?

Source
[https://forum.filezilla-project.org/viewtopic.php?f=2&t=40513&sid=d1fda044b126eb6318aa2f5da7454e14](https://forum.filezilla-project.org/viewtopic.php?f=2&t=40513&sid=d1fda044b126eb6318aa2f5da7454e14)

---

### Post by jim_deadlock on 2016-05-24
[http://ubuntuforums.org/showthread.php?t=2325481&p=13494412#post13494412](http://ubuntuforums.org/showthread.php?t=2325481&p=13494412#post13494412)

---

