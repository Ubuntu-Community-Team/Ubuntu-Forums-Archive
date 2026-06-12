---
title: "dovecot timing out."
date: 2021-07-26
forum: General Help
---

### Post by rsteinmetz70112 on 2021-07-26
I run an exim4 mail server with dovecot. I've recently begun having one account fail to get its pop3 messages. 

this seems the relevant error message.

```
Jul 25 13:59:40 thelma dovecot: pop3(rob)<230216><7bu3VPbHDPfAqAGP>: Error: Couldn't init INBOX: Timeout while waiting for lock
```

I've been looking for a way around it but looked at the /etc/dovecot file and see a lot of different older config files. 

```
# ls -ld *
drwxr-xr-x 2 root root     4096 Jul 26 15:11 conf.d
-rw-r--r-- 1 root root      525 Aug  9  2014 dovecot.conf
-rw-r--r-- 1 root root    52447 Jul 25  2011 dovecot_conf
-rw------- 1 root root    42028 Jun 24  2008 dovecot.conf.feisty
-rw-r--r-- 1 root root     4401 May 14  2014 dovecot.conf.ucf-dist
-rw------- 1 root root    39346 Jun 24  2008 dovecot.conf.ucf-old
-rw-r----- 1 root dovecot   410 Jun 29  2012 dovecot-db.conf.ext
-rw-r----- 1 root dovecot  1507 Mar 16  2016 dovecot-dict-auth.conf.ext
-rw-r----- 1 root dovecot   852 May 14  2014 dovecot-dict-sql.conf.ext
-rw-r--r-- 1 root root      525 Aug  9  2014 dovecot-new.conf
lrwxrwxrwx 1 root root       26 Apr 11  2015 dovecot.pem -> /etc/ssl/certs/dovecot.pem
-rw-r----- 1 root dovecot  5824 Aug 26  2019 dovecot-sql.conf.ext
drwx------ 2 root root     4096 Apr 11  2015 private
```

---

