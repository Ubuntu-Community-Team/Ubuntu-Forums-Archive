---
title: "sendmail problem"
date: 2006-10-17
forum: General Help
---

### Post by mitjab on 2006-10-17
i install sendmail and modifies php.ini that is like this

```

[mail function]
; For Win32 only.
SMTP = localhost
smtp_port = 25

; For Win32 only.
;sendmail_from = me@example.com

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
;sendmail_path =
sendmail_path = /usr/bin/sendmail/


```

few time sendmail works and send mail but now stop sending mail.

if i test /usr/sbin/sendmail -d0.1 -bv root i get

```

root@server:~# /usr/sbin/sendmail -d0.1 -bv root
Version 8.13.5.20060308
 Compiled with: DNSMAP LDAPMAP LDAP_REFERRALS LOG MAP_REGEX MATCHGECOS
                MILTER MIME7TO8 MIME8TO7 NAMED_BIND NETINET NETINET6 NETUNIX
                NEWDB NIS NISPLUS PIPELINING SASLv2 SCANF SOCKETMAP STARTTLS
                USERDB USE_LDAP_INIT XDEBUG

============ SYSTEM IDENTITY (after readcf) ============
      (short domain name) $w = localhost
  (canonical domain name) $j = localhost.localdomain
         (subdomain name) $m = localdomain
              (node name) $k = server
========================================================

mitjab... deliverable: mailer local, user mitjab
root@server:~#


```

what can be wrong?

---

### Post by mitjab on 2006-10-19
anyone?

---

