---
title: "bind-dns Folder Missing for Samba4 Setup in Ubuntu"
date: 2019-09-21
forum: General Help
---

### Post by theonlytalkinggoat on 2019-09-21
I am trying to setup samba to use the bind9 backend, but a folder is missing in Samba, according to the WIKI page. This seems to be consistent, as there are several files and folders that are not where they should be, according to the wiki: [https://wiki.samba.org/index.php/BIND9_DLZ_DNS_Back_End](https://wiki.samba.org/index.php/BIND9_DLZ_DNS_Back_End)

That page says there should be a folder at /usr/local/samba/bind-dns, but it's not there. I've searched the entire root directory, but the bind-dns folder doesn't exist. Anyone know where it's supposed to be?

---

### Post by theonlytalkinggoat on 2019-09-22
The version that was in the repo was 4.8. Samba is on 4.11. An upgrade fixed the issue of the folder location.

---

