---
title: "What do these sssd status message mean and how to fix?"
date: 2020-06-01
forum: General Help
---

### Post by tkwok on 2020-06-01
[B]When I run 'systemctl status sssd' I either get one of two messages. Can anyone tell me what this means and how to fix it?

```&#9679; sssd.service - System Security Services Daemon
   Loaded: loaded (/lib/systemd/system/sssd.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2020-05-29 13:48:37 EDT; 2 days ago
 Main PID: 732 (sssd)
    Tasks: 5 (limit: 4915)
   CGroup: /system.slice/sssd.service
           &#9500;&#9472; 732 /usr/sbin/sssd -i --logger=files
           &#9500;&#9472;1364 /usr/lib/x86_64-linux-gnu/sssd/sssd_be --domain hc2.local --uid 0 --gid 0 --logger=files
           &#9500;&#9472;1451 /usr/lib/x86_64-linux-gnu/sssd/sssd_nss --uid 0 --gid 0 --logger=files
           &#9500;&#9472;1452 /usr/lib/x86_64-linux-gnu/sssd/sssd_pam --uid 0 --gid 0 --logger=files
           &#9492;&#9472;1454 /usr/lib/x86_64-linux-gnu/sssd/sssd_ssh --uid 0 --gid 0 --logger=files

Jun 01 10:13:31 ubad-t1 [sssd[ldap_child[30242]: Failed to initialize credentials using keytab [MEMORY:/etc/krb5.keytab]: Preauthentication failed. Unable to create 
Jun 01 10:14:34 ubad-t1 [sssd[ldap_child[30248]: Failed to initialize credentials using keytab [MEMORY:/etc/krb5.keytab]: Preauthentication failed. Unable to create 
Jun 01 10:15:46 ubad-t1 [sssd[ldap_child[30250]: Failed to initialize credentials using keytab [MEMORY:/etc/krb5.keytab]: Preauthentication failed. Unable to create 
Jun 01 10:15:47 ubad-t1 [sssd[ldap_child[30251]: Failed to initialize credentials using keytab [MEMORY:/etc/krb5.keytab]: Preauthentication failed. Unable to create 
Jun 01 10:17:05 ubad-t1 [sssd[ldap_child[30255]: Failed to initialize credentials using keytab [MEMORY:/etc/krb5.keytab]: Preauthentication failed. Unable to create 
Jun 01 10:17:05 ubad-t1 [sssd[ldap_child[30256]: Failed to initialize credentials using keytab [MEMORY:/etc/krb5.keytab]: Preauthentication failed. Unable to create 
Jun 01 10:18:15 ubad-t1 [sssd[ldap_child[30258]: Failed to initialize credentials using keytab [MEMORY:/etc/krb5.keytab]: Preauthentication failed. Unable to create 
Jun 01 10:18:15 ubad-t1 [sssd[ldap_child[30259]: Failed to initialize credentials using keytab [MEMORY:/etc/krb5.keytab]: Preauthentication failed. Unable to create 
Jun 01 10:19:34 ubad-t1 [sssd[ldap_child[30269]: Failed to initialize credentials using keytab [MEMORY:/etc/krb5.keytab]: Preauthentication failed. Unable to create 
Jun 01 10:19:34 ubad-t1 [sssd[ldap_child[30270]: Failed to initialize credentials using keytab [MEMORY:/etc/krb5.keytab]: Preauthentication failed. Unable to create
```

Or 

```
&#9679; sssd.service - System Security Services Daemon
   Loaded: loaded (/lib/systemd/system/sssd.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2020-05-29 10:42:10 EDT; 2 days ago
 Main PID: 817 (sssd)
   CGroup: /system.slice/sssd.service
           &#9500;&#9472; 817 /usr/sbin/sssd -i --logger=files
           &#9500;&#9472;1244 /usr/lib/x86_64-linux-gnu/sssd/sssd_be --domain hc2.local --uid 0 --gid 0 --logger=files
           &#9500;&#9472;1285 /usr/lib/x86_64-linux-gnu/sssd/sssd_nss --uid 0 --gid 0 --logger=files
           &#9500;&#9472;1287 /usr/lib/x86_64-linux-gnu/sssd/sssd_pam --uid 0 --gid 0 --logger=files
           &#9492;&#9472;1288 /usr/lib/x86_64-linux-gnu/sssd/sssd_ssh --uid 0 --gid 0 --logger=files

Jun 01 10:16:49 ubad-t2 sssd[be[1244]: GSSAPI Error: Unspecified GSS failure.  Minor code may provide more information (Server not found in Kerberos database)
Jun 01 10:18:06 ubad-t2 sssd[be[1244]: GSSAPI Error: Unspecified GSS failure.  Minor code may provide more information (Server not found in Kerberos database)
Jun 01 10:18:06 ubad-t2 sssd[be[1244]: GSSAPI Error: Unspecified GSS failure.  Minor code may provide more information (Server not found in Kerberos database)
Jun 01 10:19:19 ubad-t2 sssd[be[1244]: GSSAPI Error: Unspecified GSS failure.  Minor code may provide more information (Server not found in Kerberos database)
Jun 01 10:19:22 ubad-t2 sssd[be[1244]: GSSAPI Error: Unspecified GSS failure.  Minor code may provide more information (Server not found in Kerberos database)
Jun 01 10:19:22 ubad-t2 sssd[be[1244]: GSSAPI Error: Unspecified GSS failure.  Minor code may provide more information (Server not found in Kerberos database)
Jun 01 10:20:25 ubad-t2 sssd[be[1244]: GSSAPI Error: Unspecified GSS failure.  Minor code may provide more information (Server not found in Kerberos database)
Jun 01 10:20:26 ubad-t2 sssd[be[1244]: GSSAPI Error: Unspecified GSS failure.  Minor code may provide more information (Server not found in Kerberos database)
Jun 01 10:21:53 ubad-t2 sssd[be[1244]: GSSAPI Error: Unspecified GSS failure.  Minor code may provide more information (Server not found in Kerberos database)
Jun 01 10:21:53 ubad-t2 sssd[be[1244]: GSSAPI Error: Unspecified GSS failure.  Minor code may provide more information (Server not found in Kerberos database)
```[/B]

---

