---
title: "Installing FTP"
date: 2007-03-02
forum: General Help
---

### Post by jamiehd on 2007-03-02
I have apache installed on a machine running Xubuntu and everything is working fine. But what do I need to install in order to access remotely using ftp?

Thanks,

Jamie

---

### Post by taurus on 2007-03-02
You need to install a ftp server or sshd.

```
sudo aptitude update
sudo aptitude install proftpd gproftpd
gksudo gproftpd
```
Run that last command to configure your proftpd (ftp server).

---

