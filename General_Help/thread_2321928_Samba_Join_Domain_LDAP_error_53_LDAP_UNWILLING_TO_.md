---
title: "Samba Join Domain: LDAP error 53 LDAP_UNWILLING_TO_PERFORM"
date: 2016-04-25
forum: General Help
---

### Post by Hamss on 2016-04-25
Hi,

I am using this instruction to join an existing DC: [https://wiki.samba.org/index.php/Join_an_additional_Samba_DC_to_an_existing_Active_Directory](https://wiki.samba.org/index.php/Join_an_additional_Samba_DC_to_an_existing_Active_Directory)

But I get the following error when joining to the DC:

```
# samba-tool domain join pom-pdc01.muc.pom DC -Uadministrator  --realm=MUC.POM --dns-backend=BIND9_DLZ --server pom-pdc01.muc.pom
workgroup is POM
realm is muc.pom
checking sAMAccountName
Adding CN=POM-DC02,OU=Domain Controllers,DC=muc,DC=pom
Join failed - cleaning up
checking sAMAccountName
ERROR(ldb): uncaught exception - LDAP error 53 LDAP_UNWILLING_TO_PERFORM -  <00002010: SvcErr: DSID-031A12D2, problem 5003 (WILL_NOT_PERFORM), data 0
> <>
  File "/usr/local/samba/lib/python2.7/site-packages/samba/netcmd/__init__.py", line 175, in _run
    return self.run(*args, **kwargs)
  File "/usr/local/samba/lib/python2.7/site-packages/samba/netcmd/domain.py", line 651, in run
    machinepass=machinepass, use_ntvfs=use_ntvfs, dns_backend=dns_backend)
  File "/usr/local/samba/lib/python2.7/site-packages/samba/join.py", line 1192, in join_DC
    ctx.do_join()
  File "/usr/local/samba/lib/python2.7/site-packages/samba/join.py", line 1094, in do_join
    ctx.join_add_objects()
  File "/usr/local/samba/lib/python2.7/site-packages/samba/join.py", line 544, in join_add_objects
    ctx.samdb.add(rec)

```

The error code means:
```
Indicates that the LDAP server cannot process the request because of server-defined restrictions. This error is returned for the following reasons:
The add entry request violates the server's structure rules.. OR...
The modify attribute request specifies attributes that users cannot modify...OR...
Password restrictions prevent the action...OR...
Connection restrictions prevent the action.
```

But I have no clue what exactly the problem is.
The Domain Controller was joined the domain before, but I needed to setup again due to failure.

The Kerberos Ticket was obtained successfully before.
Do you have any idea, what the problem could be?

Thanks and regards!
Hamss

---

