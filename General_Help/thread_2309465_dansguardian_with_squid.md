---
title: "dansguardian with squid"
date: 2016-01-10
forum: General Help
---

### Post by sparky-steve on 2016-01-10
Hello!

So I'm running squid with no problems, it's in transparent mode.

I'm also using shorewall, fwiw.

I've now installed dansguardian, and redirected certain local computers to it; It's running ok, except that squid is blocking everything that dansguardian is trying to do, with access denied.

I know I must be missing a simple rule in squid.conf, but so far I cannot find it.

I tried adding acl localhost 127.0.0.1 but that caused an error on restart.

Squid and Dansguardian are on the same server.

Thanks for any & all input.

-SS

---

