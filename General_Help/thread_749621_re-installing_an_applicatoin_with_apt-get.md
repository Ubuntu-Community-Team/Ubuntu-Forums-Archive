---
title: "re-installing an applicatoin with apt-get"
date: 2008-04-08
forum: General Help
---

### Post by seeker1458 on 2008-04-08
Im trying to re-install syslog-ng with all the original .conf files.  When i run

```
sudo apt-get remove syslog-ng
```

Everything runs fine, but none of the files get removed.  I still have a folder structure with all the modified syslog-ng files. Even when I try running the:

```
sudo apt-get install syslog-ng
```

command I am left with the files I created.  

How do I get a clean install of syslog-ng on my system?

---

### Post by kellemes on 2008-04-08
try..
```
sudo apt-get remove --purge syslog-ng
```
You can always manually remove the files you need to be recreated.

---

### Post by seeker1458 on 2008-04-08
I have gone in and manually removed them and when I re-install it doesn't re-create those files.  Its almost like something in not finishing completely.  But I don't get any errors or notifications.

---

### Post by seeker1458 on 2008-04-08
Ok, not exactly sure what I did different. I think I removed & purged, rebuilt the dependencies, then re-installed. I think it is working again...anyway, it is logging auth activity now!

---

