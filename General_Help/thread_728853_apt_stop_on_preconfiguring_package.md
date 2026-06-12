---
title: "apt stop on preconfiguring package"
date: 2008-03-19
forum: General Help
---

### Post by tortue17 on 2008-03-19
Hi,

Package : apt
Version : 0.7.6

I use a bash script to finish Ubuntu install by pxe.
And with this command there is a problem:

[B]yes `` | apt-get -y --force-yes -o Dpkg::Options::="--force-confdef" -o Dpkg::Options::="--force-confold" install ssh libnss-ldap libpam-ldap libpam-mount sm
bfs[/B]

Under Feisty, edgy, dapper, I have no problem, but under Gutsy after downloading package, it stop by that :
[B]
Preconfiguring packages...[/B]

Any idea ?
Thanks*
*

---

### Post by tortue17 on 2008-03-20
up

---

### Post by tortue17 on 2008-04-29
up 
Nobody can answer me ?

---

