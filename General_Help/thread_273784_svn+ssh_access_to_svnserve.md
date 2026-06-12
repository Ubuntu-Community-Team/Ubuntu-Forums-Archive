---
title: "svn+ssh access to svnserve"
date: 2006-10-08
forum: General Help
---

### Post by hecato on 2006-10-08
Hi there people.


Im trying to get a svn server up and working to do some projects at school and been able to have the repo at my house...

OK, so I do

```

svnuser@hgb-64:/repos/svn$ svnadmin create p1

```

And then:

```

svnuser@hgb-64:svnserve --foreground -r /repos/svn/ -d

```

And then only with svn
```

svnuser@hgb-64:~/Desktop$ svn info svn://localhost/p1
Ruta: p1
URL: svn://localhost/p1
Raíz del repositorio: svn://localhost/p1
UUID del repositorio: 95c9612b-541f-0410-a1e5-d5ecf45514e4
Revisión: 0
Tipo de nodo: directorio
Revisión del último cambio: 0
Fecha de último cambio: 2006-10-08 17:24:32 -0500 (dom, 08 oct 2006)

```

But when using ssh something go wrong (I dont know if I need to setup something more)

```

svnuser@hgb-64:~/Desktop$ svn info svn+ssh://localhost/p1
ssh: connect to host localhost port 22: Connection refused
svn: La conexión de red se cerró inesperadamente

```
What say there in english is "svn: the net connection is closed unexpectedly"

Tought I can autenticate with default user sally (I have uncommented the lines from conf/passwd for my test) when asking user and password... via svn:// but without +ssh.


¿Some one know what to do?

---

### Post by kochen on 2006-11-11
does SSH works on this machine?
I had a similar issue when trying to access behind a **firewall** (check that port 22 forwards to your server)

---

### Post by krismatth3 on 2006-11-11
Yeah, the error message means it can't get an ssh connection to localhost. Try:

```

apt-get install ssh

```

---

