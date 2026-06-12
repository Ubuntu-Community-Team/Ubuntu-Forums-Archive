---
title: "ubuntu equivalent for rpm -q squid"
date: 2007-06-12
forum: General Help
---

### Post by jayallen on 2007-06-12
I want to know if squid on an ubuntu server.  I'm completely new to linux and have pretty much no idea what I"m doing.    I have found instructions to see if an application is installed in redhat, but the instructions don't work in ubuntu.  Could someone tell me what the equivalent to rpm -q squid is in ubuntu so I can see if it is installed?

---

### Post by christhemonkey on 2007-06-12
If you want to check if squid is installed you could type something like:
```
dpkg-query -s squid 
```

Will tell you the status of the application.

To install squid you can do:
```
sudo apt-get install squid 
```
Sorted.

---

