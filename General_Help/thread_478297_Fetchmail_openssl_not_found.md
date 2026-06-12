---
title: "Fetchmail: openssl not found?"
date: 2007-06-19
forum: General Help
---

### Post by andrew.46 on 2007-06-19
Hi,

 I am compiling Fetchmail 6.3.8 under Ubuntu Dapper Drake and I have
the following error message:
```

configure: error: SSL support enabled, but OpenSSL not found
```

 This after running:

```
./configure --with-ssl
```

 I am a little puzzled because I actually _do_ have openssl installed:

```
andrew@ilium:~$ openssl version
OpenSSL 0.9.8a 11 Oct 2005
```

 Any thoughts on this one?

          Andrew

---

