---
title: "BUG in pure-ftpd-mysql package (universe)"
date: 2005-04-03
forum: General Help
---

### Post by punjab on 2005-04-03
Hi.

I try use pure-ftpd-mysql 1.0.19-4, but after running and attempt connect return error message like:

No such file or directory (cannot execute) /usr/sbin/pure-ftpd
I edit line 26 in pure-ftpd-wrapper to "my $daemon = '/usr/sbin/pure-ftpd**-mysql**';"

After this upgrade cannot run /usr/sbin/pure-ftpd-mysql**-mysql**
I make symbolic link ln /usr/sbin/pure-ftpd-mysql /usr/sbin/pure-ftpd-mysql**-mysql** and all works perfect.

I dont understand perl scripting and my way is "pig way".

Can somebody fix this "bug"?

---

