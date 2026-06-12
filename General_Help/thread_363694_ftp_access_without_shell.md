---
title: "ftp access without shell"
date: 2007-02-17
forum: General Help
---

### Post by mitjab on 2007-02-17
I want to create FTP access for my friend that not have a shell account in my server. he owns only one folder and i want to create ftp access to this folder for him.

can someone tell me how or give me nice tutorial?

Thx

---

### Post by taurus on 2007-02-17
```
sudo aptitude update
sudo aptitude install proftpd gproftpd
gksudo gproftpd
```

---

### Post by mitjab on 2007-02-17
i am already using proftpd and webmin but i do not know how to make this in webmin. I can not use gproftpd
 becouse this is server without gnome or any X11-server.

---

### Post by taurus on 2007-02-17
Then you need to config /etc/proftpd.conf by hand then.

---

### Post by JamieC on 2007-02-17
I take it you've configured proftpd to use system users?

Just add a user but do not permit that user shell access:
```

useradd <username> -s /bin/false

```

---

### Post by mitjab on 2007-02-17
i do this. I didn't get any question about shell access. 

how can i now make that this user can access to some folder?

Yes now users who has shell can access by ftp to their directory.

---

