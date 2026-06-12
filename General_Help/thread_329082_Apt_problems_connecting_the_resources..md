---
title: "Apt problems connecting the resources."
date: 2006-12-31
forum: General Help
---

### Post by floydo on 2006-12-31
Hello folks,

I was using Adept when it suddenly crashed and it closed with an error message. From then, apt is not working anymore. For some reason, apt tries to connect with localhost instead of archives.ubuntu.com etc.. and the connection is refused. 

sergio@sergio-desktop:~$ sudo apt-get update
Password:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  No pude conectarme a localhost:4001 (127.0.0.1). - connect (111 Conexión rechazada)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg
  No pude conectarme a localhost:4001 (127.0.0.1). - connect (111 Conexión rechazada)
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg
  No pude conectarme a localhost:4001 (127.0.0.1). - connect (111 Conexión rechazada)
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
  No pude conectarme a localhost:4001 (127.0.0.1). - connect (111 Conexión rechazada)
Err [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg
  No pude conectarme a localhost:4001 (127.0.0.1). - connect (111 Conexión rechazada)
Err [http://kubuntu.org](http://kubuntu.org) dapper Release.gpg
  No pude conectarme a localhost:4001 (127.0.0.1). - connect (111 Conexión rechazada)
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  No pude conectarme a localhost:4001 (127.0.0.1). - connect (111 Conexión rechazada)
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) dapper Release.gpg
  No pude conectarme a localhost:4001 (127.0.0.1). - connect (111 Conexión rechazada)
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) dapper-updates Release.gpg
  No pude conectarme a localhost:4001 (127.0.0.1). - connect (111 Conexión rechazada)

I guess a config file of apt got corrupted when the application Adept crashed, but I dunno which one. 'Sources.list' isnt damaged. 'Apt.conf' is empty. If I ping archive.ubuntu.com I get a normal response from its typical IP. Internet works good. The only problem is that for some reason it tries to connect localhost, dunno why.

Does anybody know whats happening?

Thank you in advance :)

---

### Post by aliyanage on 2007-01-01
Hi,

could you copy paste your sources.list file please...

```
cd /etc/apt/
cat sources.list
```

regards
aliyanage

---

