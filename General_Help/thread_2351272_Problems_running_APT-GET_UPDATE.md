---
title: "Problems running APT-GET UPDATE"
date: 2017-02-01
forum: General Help
---

### Post by juan5 on 2017-02-01
[COLOR=#000000]Hi all,[/COLOR]

[COLOR=#000000]Ubuntu 16.04[/COLOR]

[COLOR=#000000]On running;[/COLOR]
[COLOR=#000000]sudo apt-get update[/COLOR]
[COLOR=#000000]I get the following errors.

[/COLOR]> psx2001@PSX2001:~$ sudo apt-get update
[sudo] password for psx2001: 
apt-get: /usr/lib/x86_64-linux-gnu/libapt-pkg.so.5.0: version `APTPKG_5.0' not found (required by apt-get)
apt-get: /usr/lib/x86_64-linux-gnu/libapt-pkg.so.5.0: version `APTPKG_5.0' not found (required by /usr/lib/x86_64-linux-gnu/libapt-pkg.so.5.0)
apt-get: /usr/lib/x86_64-linux-gnu/libapt-pkg.so.5.0: version `APTPKG_5.0' not found (required by /usr/lib/x86_64-linux-gnu/libapt-private.so.0.0)
psx2001@PSX2001:~$ 


---

### Post by Bashing-om on 2017-02-01
juan5; Humm ...

The game is afoot !
per:
[http://packages.ubuntu.com/search?searchon=contents&keywords=libapt-pkg.so.5.0&mode=filename&suite=xenial-updates&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libapt-pkg.so.5.0&mode=filename&suite=xenial-updates&arch=any)
we are looking for libapt-pkg5.0 .
So, what have we on the system ?
```

dpkg -l libapt-pkg5.0
apt-cache policy libapt-pkg5.0

```
( is apt even able to work here ?)

[INDENT][INDENT]something just ain't right
[/INDENT][/INDENT]

---

### Post by juan5 on 2017-02-01
Hello Bashing-om
I don't know what happened 
The system was working properly and I'd try to use SYNAPTIC and didn't do nothing and I'd try to use APT-GET and got those errors 

Code:
> psx2001@PSX2001:~$ dpkg -l libapt-pkg5.0
Deseado=desconocido(U)/Instalar/eliminaR/Purgar/retener(H)
| Estado=No/Inst/ficheros-Conf/desempaqUetado/medio-conF/medio-inst(H)/espera-disparo(W)/pendienTe-disparo
|/ Err?=(ninguno)/requiere-Reinst (Estado,Err: mayúsc.=malo)
||/ Nombre         Versión      Arquitectura Descripción
+++-==============-============-============-=================================
ii  libapt-pkg5.0: 1.2.15       amd64        package management runtime librar
in  libapt-pkg5.0: <ninguna>    i386         (no hay ninguna descripción dispo
psx2001@PSX2001:~$ apt-cache policy libapt-pkg5.0
apt-cache: /usr/lib/x86_64-linux-gnu/libapt-pkg.so.5.0: version `APTPKG_5.0' not found (required by apt-cache)
apt-cache: /usr/lib/x86_64-linux-gnu/libapt-pkg.so.5.0: version `APTPKG_5.0' not found (required by /usr/lib/x86_64-linux-gnu/libapt-pkg.so.5.0)
apt-cache: /usr/lib/x86_64-linux-gnu/libapt-pkg.so.5.0: version `APTPKG_5.0' not found (required by /usr/lib/x86_64-linux-gnu/libapt-private.so.0.0)
psx2001@PSX2001:~$ 


---

### Post by Bashing-om on 2017-02-01
juan5; Humm ..

You have an older version installed:
> 
ii libapt-pkg5.0: 1.2.15 

on a fully updated system:
mine:
> 
sysop@x1604:~$ dpkg -l libapt-pkg5.0 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  libapt-pkg5.0: 1.2.19       amd64        package management runtime librar
sysop@x1604:~$

Should be.

Let's try and see if the less invasive :
```

sudo apt install --reinstall libapt-pkg5.0

```
will pull in the 1,2,19 version ; Or, what results with the attempt.

[INDENT][INDENT]won't know 'til we try
[/INDENT][/INDENT]

---

