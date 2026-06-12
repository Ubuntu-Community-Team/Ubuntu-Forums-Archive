---
title: "vsftpd - and max clients"
date: 2005-04-22
forum: General Help
---

### Post by nix4me on 2005-04-22
Hi,
I am trying to setup vsftpd with multiple user accounts that have different max_clients directives.

I need the following:
user1 - 2 users
user2 - 2 users
user3 - 1 user

Just setting max_clients to 5 does not work beacuse user1 could get 5 clients and the rest will get shutout.

Also, the multiple config file option does not allow for the max_clients directive.

Has anyone figured out a way to do this?

nix

---

