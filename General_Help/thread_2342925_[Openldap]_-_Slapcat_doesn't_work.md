---
title: "[Openldap] - Slapcat doesn't work"
date: 2016-11-11
forum: General Help
---

### Post by zoe on 2016-11-11
Hello everyone

I hope someone can help me with this strange behavior
When trying to get a backup from my running production installation using slapcat i receive this 
> [root@prodldap ~]# slapcat -n 2 > /tmp/bdbconfig.ldif
bdb_db_open: warning - no DB_CONFIG file found in directory /var/lib/ldap
Expect poor performance for suffix "dc=my-domain,dc=com".

The strange part and i repeat is that is my working production installation and the data are not located in /var/lib/ldap but in another in /opt/data path! 

> 
[root@prodldap ~]# cat /etc/openldap/slapd.conf | grep directory
# The database directory MUST exist prior to running slapd AND 
directory       /opt/data
# Indices to maintain for this directory

Why slpacat tries to find DB_CONFIG in the /var/lib? And maybe that's the reason that the > slapcat -n 2 > /tmp/bdbconfig.ldif gives an empty ldif archive

Does anyone have a clue? Thanks in advance

---

