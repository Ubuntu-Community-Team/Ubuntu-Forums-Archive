---
title: "AMPP on Ubuntu - Virtual Hosts"
date: 2012-12-31
forum: General Help
---

### Post by hypertyper on 2012-12-31
I've just spent literally hours trying to figure out how to add virtual hosts on a local AMPP stack on my 12.10 Ubuntu. I mostly looked at the following documentation, which I also used to install:

[https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual_Hosts](https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual_Hosts)

What seems to be missing is the crucial step of editing the /etc/hosts file. There is no mention of adding to the "127.0.0.1	localhost" line. If I haven't completely lost it, that's where you have to add any virtual host with the relevant ServerName (also not mentioned).

Should the following be added to the documentation:
1. Explanation and addition of "ServerName testserver" line in the virtual host file (in sites-available).
2. Configuration of /etc/hosts file with the same "testserver" name.

?

I'm a noob but maybe I won't be the last to struggle with the documentation as it is now. Is what I've done correct?

Thanks

---

