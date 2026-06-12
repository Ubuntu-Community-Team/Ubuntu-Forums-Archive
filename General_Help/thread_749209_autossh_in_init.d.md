---
title: "autossh in init.d"
date: 2008-04-08
forum: General Help
---

### Post by v5lur on 2008-04-08
Im trying to get autossh tunneling to get work when machine boots..
I saved a script in init.d called "tunnel", chmod +x tunnel, the code in file looks like this:


#! /bin/sh
autossh -i /home/x/.ssh/id_rsa -L 3306:192.168.2.106:3306 x@80.151.56.41 &

then I run update-rc.d

but it makes no tunnel connection when I reboot! If I run the line manually in terminal, it works! I cant figure out whats the problem with that.

Please help!

---

### Post by kpkeerthi on 2008-04-08
Perhaps, put that command in **/etc/rc.local**

---

### Post by v5lur on 2008-04-09
Thanx alot!! It works!

---

