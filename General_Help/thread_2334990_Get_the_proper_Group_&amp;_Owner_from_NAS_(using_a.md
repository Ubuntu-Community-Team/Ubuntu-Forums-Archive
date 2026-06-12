---
title: "Get the proper Group &amp; Owner from NAS (using autofs, sssd)"
date: 2016-08-24
forum: General Help
---

### Post by tbeaudry on 2016-08-24
Hi,

I have a NAS (netapp). with windows samba shares connect to AD. 

I would like to mount some shares from the NAS onto my ubuntu 16.04 server.    When I mount them, I get the group and owner listed as root.  I would like to get the proper group and usernames that are listed on the NAS.  I will have 20+ users connecting to the server to access the NAS, so i don't want to mount as a specific user, I just want the already established groups and owners to list when a user looks at the directory.

Here are my autofs config files

```

auto.master

/NAS /etc/auto.cifs-shares  --ghost

```

```

auto.cifs-shares

home -fstype=cifs,rw,sec=krb5 ://my-nas/home\$

```

sssd and kerberos are configured so I am able to login to the unbuntu server with my AD credentials and mount via autofs.

Thanks a lot for you help!
Thomas


[FONT=Verdana]
[/FONT]
[FONT=Verdana]
[/FONT]

---

### Post by tbeaudry on 2016-08-29
I've also tried NFS but it didn't work either.  Any help would be greatly appreciated!

---

