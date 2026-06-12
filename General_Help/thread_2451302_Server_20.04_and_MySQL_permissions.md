---
title: "Server 20.04 and MySQL permissions"
date: 2020-10-01
forum: General Help
---

### Post by patdundee on 2020-10-01
Hi Guys
Installed the new 20.04 LTS and I am running latest MySQL 8 

mysql  Ver 8.0.21-0ubuntu0.20.04.4 for Linux on x86_64 ((Ubuntu))

In 18.04 I can give a user full permissions on a database including GRANT (under Administration)

In 20.04 I cannot give them full permissions (Grant is missing)

I have tried via command line and via phpmyadmin

In command line i issue the cmd to grant all on the specific database and that comes back with OK
I then flush privileges and check but it is always missing that one

Why can i not give them the same permissions in 20.04 as they have always had in all other versions

See attached image from phpmyadmin

P[ATTACH=CONFIG]287082[/ATTACH]

Any ideas please?
Thanks

---

