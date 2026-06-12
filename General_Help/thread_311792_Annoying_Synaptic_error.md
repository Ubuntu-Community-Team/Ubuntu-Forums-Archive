---
title: "Annoying Synaptic error"
date: 2006-12-03
forum: General Help
---

### Post by Takmadeus on 2006-12-03
greetings..... I have a problem

since I istalled dapper I get this error:

```
http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.bz2: El subproceso bzip2 devolvió un código de error (2)
http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.bz2: El subproceso bzip2 devolvió un código de error (2)
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2: El subproceso bzip2 devolvió un código de error (2)
http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz: Error leyendo del servidor, el lado remoto cerró la conexión.
http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz: 416 Requested Range Not Satisfiable
http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz: Error leyendo del servidor, el lado remoto cerró la conexión.
http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz: Error leyendo del servidor, el lado remoto cerró la conexión.
http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz: Error leyendo del servidor, el lado remoto cerró la conexión.
http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz: Error leyendo del servidor, el lado remoto cerró la conexión.
http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz: Error leyendo del servidor, el lado remoto cerró la conexión.
http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz: Error leyendo del servidor, el lado remoto cerró la conexión.
http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz: Error leyendo del servidor, el lado remoto cerró la conexión.
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz: El subproceso gzip devolvió un código de error (1)
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz: El subproceso gzip devolvió un código de error (1)
```

it is very annoying since I cannot update synaptic..... is there any workaround? any ideas?

what does a bzip error code 2 mean?.... why are the servers closing the connection?

thanks in advance

---

### Post by LLRNR on 2006-12-03
Try changing your /etc/apt/sources.list file to the one found [here](http://www.psychocats.net/ubuntu/sources) (scroll down to the Dapper section).

Also, put in front of every "archive" word the two-letter prefix of your country, **except for this line**:```
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

For example, in my case, "http://archive.blah.blah" turns into "http://ro.archive.blah.blah".

Then do```
sudo aptitude update
```

See if this fixes anything. If you have a problem, scroll down to the "Troubleshooting" section in the guide I pointed to.

Good luck !

LLRNR

---

