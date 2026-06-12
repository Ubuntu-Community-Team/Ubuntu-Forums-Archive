---
title: "missing cgred service 15.10"
date: 2016-04-06
forum: General Help
---

### Post by bartosz3 on 2016-04-06
Hi,

I can't find cgred.service. Is there a way to get it working on ubuntu or does it handles the things cgred does in a different manner?

---

### Post by bartosz3 on 2016-04-07
Anyone?

---

### Post by deadflowr on 2016-04-07
Did you install the cgroup packages?
From here:[http://manpages.ubuntu.com/manpages/wily/man5/cgred.conf.5.html](http://manpages.ubuntu.com/manpages/wily/man5/cgred.conf.5.html)
it looks like the conf file comes with the cgroup-tools package.

---

### Post by bartosz3 on 2016-04-11
Of course I did. Furthermore:
me@tp:~/text$ apt-cache search  cgroup|awk '{print $1}'|xargs apt-file list |grep service
cgmanager: /lib/systemd/system/cgmanager.service
cgmanager: /lib/systemd/system/cgproxy.service

It's missing all right.

---

