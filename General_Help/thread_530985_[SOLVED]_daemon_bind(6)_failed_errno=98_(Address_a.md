---
title: "[SOLVED] daemon: bind(6) failed errno=98 (Address already in use)"
date: 2007-08-21
forum: General Help
---

### Post by cancaseiro on 2007-08-21
Hi, I have problem with ldap. I installed openldap and got a lot of errors then I thought it would be good idea to completely remove it and start from scratch but it seems that dpkg -P slapd ldap-utils libldap-2.3-0 libldap2 libldap2-dev didn't completely remove it and left old information into database:

```
root@ubuntu:/home/villem# slapd -d 16383@(#) $OpenLDAP: slapd 2.3.30 (Dec 13 2006 15:54:43) $
        buildd@palmer:/build/buildd/openldap2.3-2.3.30/debian/build/servers/slapd
daemon_init: <null>
daemon_init: listen on ldap:///
daemon_init: 1 listeners to open...
ldap_url_parse_ext(ldap:///)
daemon: bind(6) failed errno=98 (Address already in use)
daemon: bind(6) failed errno=98 (Address already in use)
slap_open_listener: failed on ldap:///
slapd stopped.
connections_destroy: nothing to destroy.

```

Does someone know how to clean the database? :confused:

---

### Post by cancaseiro on 2007-08-21
Ok I figured out what to do and removed slapd "by hand" (removed by my self not by with purge) but now I got new error: ```
Setting up slapd (2.3.30-2) ...
  Creating initial slapd configuration... done.
  Creating initial LDAP directory... bdb_db_open: Cannot access database directory /usr/local/var/openldap-data (2)
backend_startup_one: bi_db_open failed! (-1)
slap_startup failed
```

Them it!

---

### Post by cancaseiro on 2007-08-22
Ok, I just rm-ed everything that ```
dpkg -P slapd ldap-utils libldap-2.3-0 libldap2 libldap2-dev
``` left behind and now I were able to reinstall everything without errors. Hopefully I will be able to get it to work fully now.

---

