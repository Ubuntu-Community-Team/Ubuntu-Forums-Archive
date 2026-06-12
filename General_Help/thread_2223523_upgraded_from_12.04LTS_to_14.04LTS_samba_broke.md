---
title: "upgraded from 12.04LTS to 14.04LTS samba broke"
date: 2014-05-11
forum: General Help
---

### Post by abubin on 2014-05-11
there seems to be a lot of problems with samba package in 14.04.

The strange thing I am facing is that I can no longer restart samba services through /etc/init.d/samba restart. In fact all other commands like start/stop and so on does not work anymore.

Not even /etc/init.d/smbd or /etc/init.d/nmbd works. I have tried remove samba and then reinstall but still same problem.

However, a reboot will get the service running. This would be difficult as there are other services running on the server and it would be inconvenient to reboot the server each time for samba config changes.

Anyone can help?

---

### Post by deadflowr on 2014-05-11
try
```
sudo restart <servicename>
```

---

### Post by abubin on 2014-05-12
ah...didn't realize this new method of starting services for ubuntu. Thanks!!

---

