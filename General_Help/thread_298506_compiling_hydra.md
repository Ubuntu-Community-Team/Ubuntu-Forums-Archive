---
title: "compiling hydra"
date: 2006-11-12
forum: General Help
---

### Post by fifth_5 on 2006-11-12
Hey am haveing major problems installing hydra the pw cracker. have never had this problem b4 only on ubuntu. OK here is the output

```
Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
                                    ... NOT found, SSL support disabled
Get it from http://www.openssl.org
Checking for Postgres (libpq) ...
                              ... NOT found, module postgres disabled
Checking for SVN (ibsvn_client-1 libapr-0.so libaprutil-0.so) ...
                              ... NOT found, module svn disabled
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from http://www.sap.com/solutions/netweaver/linux/eval/index.asp
Checking for libssh (libssh/libssh.h) ...
                                      ... NOT found, module ssh2 disabled
Get it from http://0xbadc0de.be/ - use v0.11!

Hydra will be installed into .../bin of: /usr/local
  (change this by running ./configure --prefix=path)

```


now after this step you run make, the after that make install. but i think it is down to those missing libs why they make step throws back errors.

Any help would be cool.
Thanx

fifth

---

