---
title: "Difference between sudo and sudo bash (or root terminal)?"
date: 2013-12-01
forum: General Help
---

### Post by cogset on 2013-12-01
I was wandering what are the actual differences between using sudo or sudo bash (or the root terminal):I was under the assumption that sudo had all the privileges of root but for a short period of time,so that running a command by either using sudo,or sudo bash,or opening a root terminal would be the same as far as that particular command goes-well,I've just recently found out that a command like 

```
echo 1 > /sys/device/sd$/delete 
```

only works with sudo bash or in a root terminal,but not with plain sudo:why is that? What is the difference?

---

### Post by jdeca57 on 2013-12-01
You can find a discussion here: [http://askubuntu.com/questions/20578/sudo-redirect-output](http://askubuntu.com/questions/20578/sudo-redirect-output) but in essence sudo works on echo only and not on the redirection. If you have a root shell it works on complete environment.

---

