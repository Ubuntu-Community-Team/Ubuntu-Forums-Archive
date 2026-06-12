---
title: "autofs does not mount user home dir in edgy"
date: 2006-10-30
forum: General Help
---

### Post by mathiraj on 2006-10-30
i have two systems one running dapper and the other edgy.

My NFS and NIS servers are solaris boxes. I've configured both dapper and edgey to use NIS/NFS

Both authenticate the username/password with NIS server. But only dapper automatically mounts the user home directory. Edgy doesn't mount the user home directory with a msg "Permission Denied"

Both have identical setup.

both have the following line in auto.master
/home   /etc/auto.home

and the following line in auto.home
mathi  my_server_name:/export/home/mathi

would appreciate any suggestion/fix/workaround......

---

### Post by mathiraj on 2006-10-31
i added the following line to /etc/nsswitch.conf and the problem is gone

automount:      files nis

looks like i don't even need the auto.home file anymore....

---

